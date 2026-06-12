---
title: "[SOLVED] Actualización a Gutsy"
date: 2007-10-22
forum: Argentina Team
---

### Post by Vero1 on 2007-10-22
Hola,

Un problema. 

Al aceptar la actualización que me apareció, llega un momento en que me sale un error que dice: La suma de MD5 difiere y me sugiere ver mi conexión y tratar de nuevo.

Lo hice 2 veces y siempre pasa lo mismo.

Mi conexión funciona perfectamente, ya que no tengo problemas con Evolution o cuando descargo algun programa desde Internet.

Alguien me puede orientar por favor?

Gracias.

---

### Post by aldeluis on 2007-10-22
Puede que tu conexión a internet tenga problemas, o que el mecanismo de actualización esté fallando... yo lo he hecho y no he tenido problemas. En casa mi conexión es más lenta y he actualizado a "gutsy" con la imagen iso.

Puedes intentar bajar la imagen iso del "gutsy". Comprueba su suma md5 para ver si la imagen es fiel y si es correcta, grabaló. Al introducirlo en "fiesty" te preguntará si quieres actualizarte.

---

### Post by Vero1 on 2007-10-22
Gracias por la respuesta.

En realidad mi idea era poder evitar grabar la imágen ISO para ahorrarme mas de 5 horas de grabación como me pasó con Feisty.

En fin. Dentro de un tiempito lo grabaré.

Ahora, qué es la suma MD5 y cómo hago para saber si está bien antes de grabar?

Gracias.

---

### Post by aldeluis on 2007-10-22
La suma md5 es una forma de garantizar que la imagen que te has bajado es una copia exacta del original.

Simplificando mucho el problema: imaginate que la imagen ISO es un archivo lleno de numeros, el algoritmo md5 lo que hace es sumarlos todos, si la suma es igual a la que te han dicho [[COLOR="RoyalBlue"]aquí[/COLOR]]("http://ubuntu.c3sl.ufpr.br/releases/7.10/MD5SUMS") pues entonces estás segura de que la copia es identica.

Para hacer la suma md5 de cualquier archivo, abre el terminal y pon "md5sum nombredelarchivo".

En realidad la suma md5 es un poco más complicada de hacer que sumar todos los numeros, Tienes más información en la wikipedia: [[COLOR="RoyalBlue"]MD5[/COLOR]]("http://es.wikipedia.org/wiki/MD5")

---

### Post by Vero1 on 2007-10-22
Bueno, lo que saco en conclusión es que lo que estaba bajando por Internet no estaba bien o sea fallaba la comparación hecha por MD5, pero debe pasar con esta actualización ya que, como dije antes, no me pasa con nada mas.

A veces en Windows cuando actualizaba el Spybot salia una cruz diciendo que el checksum estaba mal. MD5 sería el checksum?
Disculpa tanta pregunta pero así aprendo:)

En cuanto a Gutsy voy a esperar un poco mas y volver a intentar.
Por otro lado estoy tratando de conseguir el CD original. Claro que tardaría unos meses en llegarme, si es que lo consigo.

---

### Post by Hei Ku on 2007-10-22
hace un clean del cache y proba de vuelta.

sudo apt-get clean

eso te va a limpiar todos los archivos bajados que no tengas instalados.

---

### Post by Vero1 on 2007-10-23
Ok Hei Ku, lo haré.

Gracias

---

### Post by Vero1 on 2007-10-23
Hei Ku,

Hice sudo apt-get clean.

A pesar de éso y de haber bajado 10 atualizaciones comunes sin problemas, cuando le toca el turno a Gutsy, me sigue saliendo el mismo error...

Me parece que voy a esperar unos días más para intentarlo.

saludos

---

### Post by faktorqm on 2007-10-23
y si haces "sudo apt-get clean" y seguido "sudo apt-get update"??

si no queres ver los cartelito podes hacer "sudo apt-get update -qq" y seguir trabajando trankila.

despues ESPERA a que el gestor de actualizaciones solito te diga que hay actualizaciones y contame como te fue. salu2!!

---

### Post by Vero1 on 2007-10-24
Hola faktorqm,
Probaré lo que me indicas y luego te digo.

gracias.

---

### Post by Vero1 on 2007-10-25
Nada que hacer. Si no es una cosa es otra.
Ahora me sale un error a autenticación de paquetes.
Le echa la culpa a la Red...

saludos

---

### Post by Hernán-Amaya on 2007-10-25
proba con lo siguiente: 

entra a synaptic, anda al menu configuración - repositorio y ahí donde dice "descarga desde" elegi "otro.." y ahi dale a selecionar mejor servidor

espero que te sirva 
suerte!

---

### Post by Vero1 on 2007-10-25
Muchas gracias por tu sugerencia.
Ya lo hice y eligió un espejo de Brasil.
Probaré nuevamente la descarga.
Los tendré al tanto.

saludos

---

### Post by Vero1 on 2007-10-26
Hola Hernán,

Lo logré! Ya tengo instalado Gutsy y funciona bien aparentemente. No perdí nada de lo que tenía. Me llevó 6 horas en total, pero ya está.

Muchísimas gracias a vos y a todos lo que me ayudaron.

saludos:popcorn:

---

### Post by Hernán-Amaya on 2007-10-26
de nada! para eso estamos para aprender unos de otros!

---

### Post by rojojuan on 2007-10-26
Un mensaje parecido me apareció cuando actualicé. 
La cuestión era que tenía instalado el Automatix.
Por si lo tenés instalado:
Yo lo solucioné así:
1.- Desintalé Automatix.
2. Borré Automatix de los repositorios.
Después de esto la actuación anduvo de 10.

---

### Post by Vero1 on 2007-10-26
Hola rojojuan,

No tenía instalado Automatix, pero Hernán dió en el clavo y al cambiar de Servidor no tuve mas problemas y estoy chocha:)

saludos

---

