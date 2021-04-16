<template>
  <form @submit.prevent="submitData">
    <div>
      <label for="name">Name: </label>
      <input type="text" v-model="newName" />
    </div>
    <div>
      <label for="phone">Phone: </label>
      <input type="text" v-model="newPhone" />
    </div>
    <div>
      <label for="email">Email: </label>
      <input type="text" v-model="newEmail" />
    </div>
    <div>
      <label for="isFavorite">Favorite</label>
      <input type="checkbox" v-model="newIsFavorite" />
    </div>
    <div>
      <button @click="newFriendContact">Create Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-contact'],
  data () {
    return {
      newName: '',
      newPhone: '',
      newEmail: '',
      newIsFavorite: '',
      newFriend: {
        id: '',
        name: '',
        phone: '',
        email: '',
        isFavorite: false
      }
    }
  },
  methods: {
    newFriendContact() {
      this.newFriend.id = new Date().toISOString();
      this.newFriend.name = this.newName;
      this.newFriend.phone = this.newPhone;
      this.newFriend.email = this.newEmail;
      this.newFriend.isFavorite = this.newIsFavorite;
    },
    submitData() {
      this.$emit('add-contact', this.newFriend);
    }
  }
}
</script>