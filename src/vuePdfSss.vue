<style src="./annotationLayer.css"></style>
<script>
import componentFactory from './componentFactory'
import pdfjsWrapper from './pdfjsWrapper'
import pdfjsWorker from 'pdfjs-dist/build/pdf.worker.js'

var PDFJS = require('pdfjs-dist/legacy/build/pdf.js')

if (process.env.VUE_ENV !== 'server') {
  if (typeof window !== 'undefined' && 'Worker' in window) {
    PDFJS.GlobalWorkerOptions.workerPort = new pdfjsWorker()
  }
}

var component = componentFactory(pdfjsWrapper(PDFJS))
component.PDFJS = PDFJS

export default component
</script>
