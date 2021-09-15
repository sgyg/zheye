<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <!-- <cloumn-list :list="list"></cloumn-list> -->
    <validate-form @form-submit="formSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <validate-input
          :rules="emailRules"
          placeholder="请输入邮箱地址"
          type="text"
          v-model="emailVal"
        ></validate-input>
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <validate-input
          v-model="password"
          :rules="passwordRules"
          placeholder="请输入密码"
          type="password"
        ></validate-input>
      </div>
      <template #submit>
        <span class="btn btn-danger">提交</span>
      </template>
    </validate-form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
// import CloumnList, { ColumnProps } from './components/ColumnList.vue'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import ValidateForm from './components/ValidateForm.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const currentUser: UserProps = {
  isLogin: true,
  name: 'shadiao'
}
export default defineComponent({
  name: 'App',
  components: {
    // CloumnList,
    GlobalHeader,
    ValidateInput,
    ValidateForm
  },
  setup () {
    const password = ref('')
    const emailVal = ref('')
    const emailRules: RulesProp = [
      { type: 'reqired', message: '电子邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]
    const passwordRules: RulesProp = [
      { type: 'reqired', message: '密码不能为空' }
    ]
    const formSubmit = (result: boolean) => {
      console.log(result)
    }
    return {
      // list: testData,
      currentUser,
      emailRules,
      password,
      passwordRules,
      formSubmit,
      emailVal
    }
  }
})
</script>

<style>
</style>
