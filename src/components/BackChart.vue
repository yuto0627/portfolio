<script>
import { Radar } from 'vue-chartjs';

export default {
  name: 'BackChart',
  extends: Radar,
  data () {
    return {
      data: {
        labels: [],
        datasets: [
          {
            label: 'Back-end',
            data: [],
            backgroundColor: [
              'rgba(15,136,57,0.2)',
            ],
            borderColor: [
              'rgba(15, 136, 57, 1)',
              'rgba(54, 162, 235, 1)',
              'rgba(255, 206, 86, 1)',
              'rgba(75, 192, 192, 1)',
              'rgba(153, 102, 255, 1)',
              'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
          },
        ]
      },
      options: {
        scale: {
          ticks: {
            beginAtZero:true,
            max:5,
            min:0
          }
        }
      }
    }
  },
  mounted () {
    this.getSkills()
    this.renderChart(this.data, this.options)
  },
  methods: {
    getSkills(){
      const frontSkillInfo = this.$store.getters.getSkills('back-end')
      frontSkillInfo.skills.forEach((skill) => {
        this.data.labels.push(skill.name)
        this.data.datasets[0].data.push(skill.score)
      })
    }
  }
}
</script>
