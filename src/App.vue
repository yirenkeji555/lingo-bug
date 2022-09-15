<script setup lang="ts">
import { computed, ref } from "vue"
import {Setup, World, OrbitCamera,AreaLight, Model, DirectionalLight,SkyLight,AmbientLight } from "lingo3d-vue"
//global state that determines the selected object
//定义选中物体的全局状态

const arrowPosition = ref({ x:0,y:0,z:0 })
const userInfo = ref({ avatar: '',nickname:'' })
const animation = ref("idle")
const headMsg = 'xxx'
const modelName = 'ty'
const moveEnd = function() {
}
const clickMap = function(e:any) {

}
</script>
<style>

	.avatar-info {
		text-align: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		color: white;
		width: 100px;
		margin-left: -50px;
		margin-top: -75px;
		position: absolute;
		align-items: auto;
	}
	
	.avata-img {
		border: 1px solid greenyellow;
		display: block;
		margin: auto;
		width: 38px;
		height: 38px;
		border-radius: 50%;
	}
	
	.avatar-name {
		width: 50px;
		border-radius: 3px;
		font-size: 8px;
		background-color: rgba(255, 255, 255, 0.55);
		color: rebeccapurple;
		height: 20px;
		line-height: 20px;
		overflow: hidden;
		position: absolute;
		left: 25px;
		top: 30px;
	}
	
	.header-msg {
		/* border: 1px solid white; */
		width: 100px;
		overflow: hidden;
		margin-left: -50px;
		/* margin-top: -65px; */
		background-color: rgba(255, 255, 255, 0.55);
		color: rebeccapurple;
		border-radius: 3px;
		display: flex;
		align-items: center;
		position: absolute;
	}
	
	.header-msg-text {
		padding-left: 5px;
		text-align: center;
		display: inline-block;
		overflow: auto;
		color: white;
		width: 100%;
		font-size: 8px;
	}
</style>


<template>
  <World :pixelRatio="0.5" color="rgb(80, 80, 150)" defaultLight="//moretime.oss-cn-shanghai.aliyuncs.com/mod/4k.hdr" :bloomStrength="1" :bloomThreshold="0.5">
			
			<SkyLight ref="skylight" :intensity="2" color="#c59a59" groundColor="black" :bloom="true" :x="1806.12"
				:y="1426.22" :z="-3958.12" :helper="false" />
			<DirectionalLight :x="0" :y="0" :z="0" :scale="10" color="#000" :helper="false" :intensity="100"
				:animation="{rotationX: [0, 45, 90, 135, 180, 225, 270, 315, 360],rotationZ: [0, 45, 90, 135, 180, 225, 270, 315, 360]}" />
			<AmbientLight ref="skylight2" :x="98.27" :y="259.09" :z="-70.68" :scale="10" color="red" :helper="false" />
			<AreaLight :helper="false" :x="131.69" :y="75" :z="0" :width="100" :height="1000" color="#452590" :scale="5"
				:intensity="5"
				:animation="{rotationX: [0, 45, 90, 135, 180, 225, 270, 315, 360],rotationZ: [0, 45, 90, 135, 180, 225, 270, 315, 360]}" />
			
			<!-- <AreaLight :helper="false" :x="0" :y="75" :z="0" :width="100" :height="1000" color="#452590" :scale="5"
				:intensity="5"
				:animation="{rotationX: [0, 45, 90, 135, 180, 225, 270, 315, 360],rotationZ: [0, 45, 90, 135, 180, 225, 270, 315, 360]}" /> -->
			
			<!-- <AreaLight :helper="false" :x="0" :y="0" :z="0" :width="100" :height="1000" color="red" :scale="1"
				:intensity="5" :animation="{rotationX: [0, 45, 90, 135, 180, 225, 270, 315, 360]}" /> -->
			
			<!-- <DirectionalLight :x="-2081.42" :y="-8.41" :z="512.01" />
				
				<PointLight 
					:x="-74.56" 
					:y="207.7" 
					:z="524.73" 
					color="#9a10d8"
					:scale="100"
					:animation="{rotationY: [0, 45, 90, 135, 180, 225, 270, 315, 360] }"
					/> -->
			<!--  -->
			<Setup default-light="studio" color="transparent" />
			<Model physics="map" :scale="10" :rotationY="180" @click="clickMap" ref="mapModel"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/Nightclub1-v1.glb"></Model>
			
			<Model :scale="2" :x="-111.13" :y="-310.16" :z="-1400.06" :height="900" :width="900" :depth="900"
				:rotationX="180" :rotationY="0" :rotationZ="180"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/speakers-v2.glb"></Model>
			<Model :scale="2" :x="125.00" :y="-310.16" :z="-1400.06" :height="900" :width="900" :depth="900"
				:rotationX="180" :rotationY="0" :rotationZ="180"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/speakers-v2.glb"></Model>
			
			
			<Model :x="481.60" :y="-120.44" :z="-1925.42" :scale="2" animation="dance"
				:animations="{dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing-dance.fbx'}"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing.fbx"></Model>
			<Model :x="-481.60" :y="-120.44" :z="-1925.42" :scale="2"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance.fbx" animation="dance" :animations="{ dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance-dance.fbx' }"></Model>
			
			
			<Model :x="301.60" :y="-340.44" :z="-100" :scale="2" animation="dance"
				:animations="{dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing-dance.fbx'}"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing.fbx"></Model>
			
			<Model :x="-201.60" :y="-340.44" :z="-100" :scale="2"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance.fbx" animation="dance"
				:animations="{ dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance-dance.fbx' }">
			</Model>
			
			<Model :x="301.60" :y="-340.44" :z="100" :scale="2" animation="dance"
				:animations="{dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing-dance.fbx'}"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/samba-dancing.fbx"></Model>
			
			<Model :x="-201.60" :y="-340.44" :z="100" :scale="2"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance.fbx" animation="dance"
				:animations="{ dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/sexy-dance-dance.fbx' }">
			</Model>
			
			
			<Model :x="0" :y="-120.44" :z="-1925.42" :scale="2"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/alfred.fbx" animation="dance"
				:animations="{ dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/alfred-dance.fbx' }"></Model>
			
			
			
			<Model :x="0" :y="-140.44" :z="1000.42" :scale="2" :rotationY="250"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/Unity2Skfb-v1.glb"></Model>
			
			
			
			<Model :x="0" :rotationY="180" :y="-240.44" :z="-1505.42" :scale="3.5"
				src="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/dj_table2.glb">
					<Find id="Cube_1_0" name="Cube_1_0" texture="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/dj.jpeg">
					</Find>
					<Find id="Cube_2_0" name="Cube_2_0" texture="https://moretime.oss-cn-shanghai.aliyuncs.com/mod/dj.jpeg">
					</Find>
			</Model>
			
			
			
			<ThirdPersonCamera ref="thirdcamera" :innerY="50" :minPolarAngle="120" :maxPolarAngle="120" :lockTargetRotation="false" active target="person"
				mouseControl="drag">
				<Model id="person" ref="person" :depth="9999" :scale="1"
					:moveTo="[arrowPosition.x, undefined, arrowPosition.z, 3]" @MoveToEnd="moveEnd"
					:lookTo="[arrowPosition.x, undefined, arrowPosition.z, 0.1]" physics="character"
					:animation="animation" :animations="{
					idle: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/'+modelName+'-idle.fbx',
					tang: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/'+modelName+'-tang.fbx',
					hi: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/'+modelName+'-hi.fbx',
					walking: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/'+modelName+'-walking.fbx',
					dance: 'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/'+modelName+'-dance.fbx'
				}" :src="'https://moretime.oss-cn-shanghai.aliyuncs.com/mod/' + modelName + '.fbx'">
					<HTML>
						<div class="avatar-info">
							<img class="avata-img" :src="userInfo.avatar || '/static/logo.png'" />
							<span class="avatar-name">{{userInfo.nickname || '无名氏'}}</span>
						</div>
						<div class="header-msg" v-show="headMsg">
							<uni-icons style="padding-left: 3px;" type="chat-filled" color="white" size="14">
							</uni-icons>
							<span class="header-msg-text">{{headMsg}}</span>
						</div>
					</HTML>
				</Model>
			</ThirdPersonCamera>
			
		</World>
</template>
