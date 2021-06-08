<script>
// 	new Dropzone.on('addedfile', function(file) {
// 		console.log("ash")

// });
Dropzone.on("addedfile", function(file) {
         var reader = new FileReader();
        reader.onload = function(event) {
           // event.target.result contains base64 encoded image
            console.log(event.target.result);
        };
        reader.readAsDataURL(file);
    });
	const fileFetch = () => {
		console.log("Hello")
		const fileSelector = document.getElementById('input-file')
	console.log(fileSelector)
	if(fileSelector != null){
		fileSelector.addEventListener('change', (event) => {
		// const file = files[0];
		const fileList = event.target.result;
		console.log(fileList);
		   
		var fr=new FileReader();
            fr.onload=function(){
                document.getElementById('content-target')
                        .textContent=fr.result;
            }
              
            fr.readAsText(this.files[0]);
        })
  }
	}
	

</script>

<main>
	
	<form action="/" class="dropzone" >
        <div class="fallback">
			<label for="input-file">Specify a file:</label><br>
          <input name="file" type="file" id="input-file" on:input={fileFetch} />
        </div>
      </form>
	  <div class="preview">
		<textarea id="content-target"></textarea>
	  </div>
</main>

<style>
	main {
		display:grid;
		/* text-align: center; */
		grid-template-columns: 1fr 1fr;
		column-gap: 20px;
		padding: 2em;
		max-width: 240px;
		margin: 0 auto;
		
	}
	.preview {
		padding: 20px;
		background-color: antiquewhite;
	}
	
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>