<template>
    <el-table :data="tableData5" style="width: 100%">
        <el-table-column type="expand">
            <template slot-scope="props">
                <el-form label-position="left" inline class="demo-table-expand">
                    <el-form-item label="订单编号">
                        <span>{{ props.row.orderId }}</span>
                    </el-form-item>
                    <el-form-item label="支付时间">
                        <span>{{ props.row.payTime }}</span>
                    </el-form-item>
                    <el-form-item label="价格">
                        <span>{{ props.row.price }}</span>
                    </el-form-item>
                    <el-form-item label="分类">
                        <span>{{ props.row.size }}</span>
                    </el-form-item>
                    <el-form-item label="收货地址">
                        <span>{{ props.row.address }}</span>
                    </el-form-item>
                    <el-form-item label="快递信息">
                        <span>{{ props.row.information }}</span>
                    </el-form-item>
                </el-form>
            </template>
        </el-table-column>
        <el-table-column label="订单号" prop="orderId">
        </el-table-column>
        <el-table-column label="收货人" prop="receiver">
        </el-table-column>
        <el-table-column label="电话" prop="telephone">
        </el-table-column>
        <el-table-column label="地址" prop="address">
        </el-table-column>
    </el-table>
</template>

<style>
.demo-table-expand {
  font-size: 0;
}
.demo-table-expand label {
  width: 90px;
  color: #99a9bf;
}
.demo-table-expand .el-form-item {
  margin-right: 0;
  margin-bottom: 0;
  width: 50%;
}
</style>

<script>
export default {
  data() {
    return {
      tableData5: []
    };
  },
  created() {
    this.getOrderByState();
  },
  methods: {
    getOrderByState(state) {
      let that = this;
      this.$ajax
        .get("/first/orderAllByState", {
          params: {
            state: "2",
            page: "1",
            pageSize: "100"
          }
        })
        .then(function(res) {
          console.log(res.data.content);
          that.tableData5 = res.data.content;
        });
    }
  }
};
</script>
