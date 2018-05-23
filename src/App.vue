<template>
  <div id="app">
<fieldset>
    <legend>杨超文制作的录入系统</legend>
      <div>
          <span>姓名:</span>
          <input type="text" name="" placeholder="请输入姓名" v-model="newStudent.name">
      </div>

      <div>
          <span>年龄:</span>
          <input type="text" name="" placeholder="请输入年龄" v-model="newStudent.age">
      </div>

      <div>
          <span>性别:</span>
          <select v-model="newStudent.sex">
              <option value="男">男</option>
              <option value="女">女</option>
          </select>
      </div>

      <div>
          <span>手机号码:</span>
          <input type="text" name="" placeholder="请输入手机号码" v-model="newStudent.phone">
      </div>

      <button @click="addStudent()">创建新用户</button>

  </fieldset>

  <table>
    <thead>
        <tr>
            <td>姓名</td>
            <td>性别</td>
            <td>年龄</td>
            <td>手机</td>
            <td>删除</td>
        </tr>
    </thead>
    <tbody>
        <tr v-for="(p,index) in personal">
            <td>{{p.name}}</td>
            <td>{{p.age}}</td>
            <td>{{p.sex}}</td>
            <td>{{p.phone}}</td>
            <td>
              <button @click="removeStudent()">删除</button>
            </td>
        </tr>
    </tbody>
  </table>


</div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
          personal:[
              {name:"张三",age:18,sex:"男",phone:"13812828139"},
              {name:"李四",age:28,sex:"女",phone:"13811228139"},
              {name:"赵武",age:48,sex:"女",phone:"13452828139"},
              {name:"王柳",age:15,sex:"男",phone:"13344456139"},
          ],
          newStudent:{name:"",age:"",sex:"男",phone:""}
    }
  },
methods:{
        addStudent(){
          if(this.newStudent.name ===""){
              alert("请输入姓名");
              return;
          }
          if(this.newStudent.age <= 0){
              alert("请输入正确的年龄");
              return;
          }
          if(this.newStudent.phone === ""){
              alert("请输入手机号码");
              return;
          }

            this.personal.unshift(this.newStudent);
            this.newStudent= {name:"",age:"",sex:"男",phone:""}

        },

        removeStudent(index){
           this.personal.splice(index,1)
        }


}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width:600px;
  margin:100px auto;

}
fieldset{
  border:2px solid orangered;
}
fieldset legend{
  font-size: 18px;
}
fieldset input{
  width:300px;
  height: 30px;
  margin:10px;
}
fieldset select{
  margin:10px;
  height: 30px;
}
fieldset button{
  height: 30px;
  background-color: orangered;
  color:#fff;
}
table{
  width:600px;
  text-align: center;
  border:2px solid orangered;
  margin-top: 20px;

}
table thead{
  background-color: orangered;
}
table button{
  background-color: orangered;
  color:white;
}

</style>
