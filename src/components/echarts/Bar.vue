<template>
  <div class="bar">
    <div style="width:400px;height:400px;" :id="echarts" class="echarts" ref="echarts">
    </div>
  </div>
</template>

<script>
  export default {
    name:'bar',
    props: {
      chartData: {
        type: Array,
        default: () => []
      }
    },
    data() {
      return {
      };
    },
    methods: {
      drawCharts() {
        var myChart = echarts.init(document.getElementById(this.echarts));
        myChart.setOption({
          tooltip: {
            trigger: 'item',
            formatter: '{a} <br/>{b}: {c} ({d}%)'
          },
          legend: {
            orient: 'vertical',
            x: 'left',
            data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎']
          },
          series: [
            {
              name: '访问来源',
              type: 'pie',
              radius: ['50%', '70%'],
              avoidLabelOverlap: false,
              label: {
                normal: {
                  show: false,
                  position: 'center'
                },
                emphasis: {
                  show: true,
                  textStyle: {
                    fontSize: '30',
                    fontWeight: 'bold'
                  }
                }
              },
              labelLine: {
                normal: {
                  show: false
                }
              },
              data: this.chartData
            }
          ]
        });
      }
    },
    computed: {
      echarts() {
        return 'echarts' + Math.random() * 100000;
      }
    },
    mounted() {
      this.drawCharts();
    },
    components: {}
  };
</script>

<style></style>