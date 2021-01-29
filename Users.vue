<template>
<v-layout
  row wrap pt-5 text-xs-center
  style="max-width:500px;margin:0 auto"
>
  <v-flex xs12>
    <h1>Users</h1>
    <p>유저를 검색해주세요</p>
    <!-- <p>이 유저는 현재 유저 번호가 {{ userId }}입니다.</p>
    {{ $route.params.name }}
    <h1>그룹: {{ $route.query.group }}</h1>
    <h1>카테고리: {{ $route.query.category }}</h1>
    <h1>이름: {{ $route.query.name }}</h1>
    <h1>주소: {{ $route.query.address }}</h1> -->
  </v-flex>

  <v-flex xs12>
    <v-text-field
      v-model="userId"
      label="유저번호를 입력하세요."
    ></v-text-field>
    <v-btn @click="$router.push({
      name:'users-detail', 
      params:{
        id:userId
      }
    })">검색</v-btn>
  </v-flex>
  <v-flex xs12>
    <router-view></router-view>
  </v-flex>
</v-layout>
</template>

<script>
export default {
  // computed:{
  //   userId(){
  //     return this.$route.params.userId   // route.js --> path: '/users/:userId',
  //   }
  // },
  data(){
    return {
      userId : null
    }
  },
  created(){
    //console.log("router", this.$router)
    //console.log("route", this.$route)
    console.log("created") // router guard -> 컴포넌트가 생성되기전에 실행
  },
  destroyed(){
    console.log("destroyed") // 이페이지가 없어질때, 부셔질때 실행
  },
  beforeRouteEnter (to, from, next){
    console.log('before Enter')
    next()
  },
  beforeRouteLeave(to, from, next){ //라우터가 이 페이지를 떠나기 직전에
    console.log('before Leave')
    next()
  }
  
  
}
</script>