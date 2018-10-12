Comando para construir imagen en docker:
docker build -t juansalvadorg/orbis-training-docker:0.1.0 .

Comando para subir imagen a docker hub:
docker login
docker push juansalvadorg/orbis-training-docker

Comando para cambiar tag de imagen docker:
docker tag 05aae1ce4684 juansalvadorg/orbis-training-docker:0.2.0

Comando para ejecutar npm install en el contenedor:
Accion sin definir workdir: Muestra error ya que por defecto el workdir de un contenedor es la raiz y nuestro package.json se encontraba dentro de la carpeta app/

*docker run -v $PWD:/app juansalvadorg/orbis-training-docker:1.0.0 npm install 

Acción con workdir: Se ejecuto el comando npm install satisfactoriamente ya que el contenedor se encontraba posicionado dentro de la carpeta /app luego de realizar el volumeo de los archivos.

*docker run -v $PWD:/app -w /app juansalvadorg/orbis-training-docker:1.0.0 npm install 