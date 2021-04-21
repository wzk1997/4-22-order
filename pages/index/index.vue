<template>
	<view class="content">
			<view class="header">
				<text 
					:class="['header-item', active === index ? 'active': '']" 
					v-for="(item,index) in tabBarData" 
					:key='index' 
					@tap="clickItem(index)"
				>
					<text class="badge">{{index}}</text>
					{{item}}
				</text>
			</view>
			<swiper 
				style="height: calc(100vh - 70upx)"
				@change="handlePanelChange"
				:current="active"
			>
				<swiper-item
					v-for="(item,index) in tabBarData"
					:key='index' 
				>
					<scroll-view class="product-list-wrapper" :scroll-y="true" :show-scrollbar="true">
						<view class="product-card" v-for="(_, i) in 4" :key="i">
							<view class="shop-header">
								<view class="name">
									<text>icon</text>
									<text class="shop-name">cdf会员购北京</text>
									<text>></text>
								</view>
								<view class="action">
									<text>图片</text>
								</view>
							</view>
							<view class="product-list">
								<view v-for="_, index in 2" :key="index" style="margin-bottom: 10px;">
									<view class="product">
										<image src="https://picsum.photos/200/200"></image>
										<view class="desc">
											<view class="title">
												<text>这是名字</text>
												<text>￥价格</text>
											</view>
											<view>
												<text>创建时间：</text>
												<text>xxxx-xx-xx xx:xx:xx</text>
											</view>
											<view>
												<text>锁单时间：</text>
												<text>xxxx-xx-xx xx:xx:xx</text>
											</view>
											<view>
												<text>支付时间：</text>
												<text>去支付订单 ></text>
											</view>
										</view>
									</view>
									<view class="footer">
										<button>再来一单</button>
										<button open-type="share">分享得500积分</button>
									</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabBarData:['全部','待下单','待结算','已结算','已作废'],
				active: 0,
				number: 0,
				itemList:[
					{
						id:0,
						shopName:'cdf会员购北京',
						image:'',
						name:'肌肤之钥光凝前霜 37MLx2',
						price:178,
						startTime:'2020-09-01 17:22:03',
						endTime:'2020-09-01 17:22:03',
						shopNum:12
						
					},
				]
			}
		},
		onLoad() {
			
		},
		methods: {
			clickItem(index){
				this.active=index
			},
			handlePanelChange({detail: {current}}){
				if(this.active === current) return
				this.active = current
			}
		},
	}
</script>

<style>
.content{
	background-color: #f5f5f5;
	min-height: 100vh;
	display:flex;
	flex-direction: column;
}
.header{
	display: flex;
	justify-content: space-between;
	padding: 0 40upx;
	height: 70upx;
	align-items: center;
	background-color: #FFFFFF;
	color: #666;
	padding-bottom: 5rpx;
	
}
.header > text{
	position: relative;
}
.active{
	color: #FF0000;
	position: relative;
}
.active::after{
	width: 100% !important;
}
.header-item{
	font-size: 28rpx;
	height: 100%;
	display: block;
	line-height: 70upx;
	font-weight: bold;
}
.badge{
	position: absolute;
	color: #FFFFFF;
	background-color: #FF0000;
	line-height: 1;
	width: fit-content;
	padding: 5upx 15upx;
	font-size: 24upx;
	border-radius: 100px;
	transform: scale(0.7);
	right: -20px;
	top: 0;
}
.header-item::after{
	position: absolute;
	content: '';
	display: block;
	width: 0;
	height: 3px;
	background: #FF0000;
	bottom: 0;
	left: 50%;
	transform: translateX(-50%);
	transition: all .2s cubic-bezier(0.4, 1, 0.2, 1);
	/* padding-bottom: 10upx; */
}

/* 商品 */
.product-list-wrapper{
	padding: 20px 0;
	flex: 1;
	height: calc(100vh - 70upx);
	width: 100%;
	box-sizing: border-box;
}
.product-list-wrapper::-webkit-scrollbar{
	display: none;
}
.product-card{
	width: calc(100% - 30px);
	box-sizing: border-box;
	padding: 0;
	background-color: #FFFFFF;
	border-radius: 10px;
	margin-bottom: 10px;
	margin: 0 15px 10px;
}
.shop-header{
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	font-size: 28upx;
	color: #666;
	border-bottom: #00000011 1px solid;
	padding: 10px 20px;
}
.shop-header .shop-name{
	margin-left: 10px;
	margin-right: 10px;
}
.product-list{
	padding: 10px 20px;
}
.product{
	display: flex;
	align-items: center;
	font-size: 24upx;
	color: #999;
}
.product:last-child{
	margin-bottom: 0;
}
.product .title{
	display: flex;
	align-items: center;
	font-size: 28upx;
	color: #333;
}
.product image{
	width: 150upx;
	height: 150upx;
	box-shadow: 0px 2px 5px #00000055;
	border-radius: 3px;
	margin-right: 10px;
}
.desc{
	display: flex;
	flex-direction: column;
	height: 150upx;
	justify-content: space-between;
	padding: 5upx 0 ;
	box-sizing: border-box;
}
.footer{
	text-align: right;
}
.footer > button{
	display: inline-block;
	background-color: transparent;
	font-size: 24upx;
	border-radius: 100px;
	border: 1px #f5f5f5 solid;
	box-shadow: none !important;
	margin-top: 20px;
	padding: 6px 13px;
	line-height: 1;
	
}
.footer > button:nth-child(1){
	margin-right: 10px;
	border-color: #999;
	color: #999;
}
.footer > button:nth-child(2){
	border-color:  #FF0000;
	color: #FF0000;
}
</style>
