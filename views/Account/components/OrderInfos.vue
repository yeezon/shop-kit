<docs>
## AccountOrderInfos Docs
</docs>

<template>
<div class="account-order-infos" data-com="AccountOrderInfos">
  <div class="s-title">
    <SkIcon class="s-title_icon" name="order" />
    <span class="s-title_text">我的订单</span>
  </div>
  <div class="s-links">
    <button @click="fnTo('/account/orders#wait_pay')" class="s-link">
      <SkIcon class="s-icon" name="order_wait_pay" />
      <span class="s-cont">
        <span class="s-label">待付款</span>
        <span v-if="waitPay" class="s-tip">{{ waitPay }}</span>
      </span>
    </button>
    <button @click="fnTo('/account/orders#wait_get')" class="s-link">
      <SkIcon class="s-icon" name="order_wait_get" />
      <span class="s-cont">
        <span class="s-label">待收货</span>
        <span v-if="waitGet" class="s-tip">{{ waitGet }}</span>
      </span>
    </button>
    <button @click="fnTo('/account/orders#comments')" class="s-link">
      <SkIcon class="s-icon" name="order_comments" />
      <span class="s-cont">
        <span class="s-label">待评价</span>
      </span>
    </button>
    <!-- <button @click="fnTo('/account/orders#completed')" class="s-link">
      <SkIcon class="s-icon" name="order_completed" />
      <span class="s-cont">
        <span class="s-label">已完成</span>
      </span>
    </button> -->
    <button @click="fnTo('/account/services/orders')" class="s-link i-services">
      <SkIcon class="s-icon" name="order_services" />
      <span class="s-cont">
        <span class="s-label">退换/售后</span>
      </span>
    </button>
    <button @click="fnTo('/account/orders')" class="s-link i-order_all">
      <SkIcon class="s-icon" name="order_all" />
      <span class="s-cont">
        <span class="s-label">全部订单</span>
      </span>
    </button>
  </div>
  <div class="s-items">
    <orders-lite></orders-lite>
  </div>
</div>
</template>

<script>
import OrdersLite from './OrdersLite.vue'

export default {
  name: 'AccountOrderInfos',
  components: {
    OrdersLite
  },
  props: {
    waitPay: {
      type: Number,
      default: null
    },
    waitGet: {
      type: Number,
      default: null
    }
  },
  methods: {
    fnTo (path) {
      this.$router.push(path)
    }
  }
}
</script>

<style scoped>
.account-order-infos {
  background-color: #fff;
  border: 0 solid #ddd;
  border-width: var(--1px);
  border-radius: 3px;
}
.s-title {
  padding: 15px 20px;
  border: 0 solid #d5d5d5;
  border-width: 0 0 var(--1px);
  color: #333;
}
.s-title_icon {
  display: none;
}
.s-title_text {
  font-size: 16px;
}
.s-links {
  display: flex;
  padding: 0 15px;
}
.s-link {
  flex: 1;
  display: block;
  margin: 0;
  padding: 14px 0;
  outline: none;
  border: none;
  background-color: #fff;
}
.s-icon {
  display: block;
  margin: 0 auto 8px;
  font-size: 30px;
  color: #999;
}
.s-label {
  display: inline-block;
  font-size: 12px;
}
.s-cont {
  position: relative;
  display: inline-block;
}
.s-tip {
  position: absolute;
  top: -43px;
  right: -8px;
  width: 16px;
  height: 16px;
  line-height: 16px;
  border: 1.5px solid currentColor;
  border-radius: 50%;
  color: #f44;
  background-color: #fff;
  font-size: 10px;
  font-weight: bold;
}

@media screen and (max-width: 768px) {
  .account-order-infos {
    border-width: var(--1px) 0;
    border-radius: 0;
  }
  .s-title {
    padding: 10px 15px;
  }
  .s-title_icon {
    display: inline-block;
    margin: 0 6px 0 0;
    font-size: 18px;
    color: #999;
  }
  .s-title_text {
    font-size: 14px;
  }
  .s-links {
    padding: 0;
  }
  .s-link.i-services {
    display: none;
  }
  .s-items {
    display: none;
  }
}
</style>
