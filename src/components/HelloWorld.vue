<template>
	<div class="hello">
		<button @click="openApp()">点击打开APP</button>
		<button @click="openxl()">唤醒新浪</button>
	</div>
</template>

<script>
	import CallApp from "callapp-lib";
	export default {
		name: 'HelloWorld',
		data() {
			return {
				msg: 'Welcome to Your Vue.js App'
			}
		},
		methods:{
			openApp(){
				this.openWx();
			},
			openWx () {
				const options = {
					scheme: { 
						protocol: 'ykshortvideo', // 就是你要打开的 APP 的标识 必填
					},
					intent: {  //  安卓原生谷歌浏览器必须传递 Intent 协议地址，才能唤起 APP。
						package: 'com.youku.shortvideo',
						scheme: "ykshortvideo"
					},
					//apple store
					appstore: 'https://itunes.apple.com/cn/app/id1383186862',
					//应用宝
					yingyongbao: 'https://sj.qq.com/myapp/detail.htm?apkName=com.youku.shortvideo', // 去应用宝商店
					fallback: 'https://dianliu.youku.com/service/download',
					timeout: 2000,
				};
				const callLib = new CallApp(options);
				callLib.open({});
			},
			openxl(){
				
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
	
</style>