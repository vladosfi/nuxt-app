<script setup lang="ts">
const route = useRoute();
type Character = {
  id: string;
  name: string;
  image: string;
  status: string;
  species: string;
  location: {
    name: string;
  };
};
const query = gql`
  query getCharacter {
    character(id: ${route.params.id}) {
        name
        image
        status
        id
        species
        location {
          name
        }
    }
  }
`;
const { data, error } = await useAsyncQuery<character>(query);
</script>

<template>
  <div>
    <CharacterCard
      :id="data.character.id"
      :name="data.character.name"
      :image="data.character.image"
      :status="data.character.status"
      :species="data.character.species"
      :location="data.character.location.name"
    />
  </div>
</template>
