---
title: "Sony NW e005 lo hice andar pero quiero ejecutar el programa sin hacerlo desde consola"
date: 2007-11-03
forum: Argentina Team
---

### Post by valucha on 2007-11-03
[COLOR="DarkOrchid"]bueno, la idea es que pude hacer andar el pu,,,sony feo de mi mama en ubuntu, ya que en windows no me dejaba :S y el
 tema es que se los quiero simplificar y queria ver si podria armar algo de forma tal que ella haga click, le aparezca el programa, pase las canciones, desmonte y listo.

Lo que pasa es que mi mamá no se va a poner a hacer comandos en la consola, y quiero que se independice con el tema de pedirme que le cambie las canciones :(.

Para hacerlo funcionar... segui esta guia:
[http://www.elmodem.com/archivo/2007/05/29/sony-walkman-series-nw-e00x-en-linux/](http://www.elmodem.com/archivo/2007/05/29/sony-walkman-series-nw-e00x-en-linux/)
que no es más que copiar 2 archivos en el mp3.

Luego, tengo que ejecutarlo haciendo esto en consola
cacho@Notebook:~$ cd /media/disk
cacho@Notebook:/media/disk$ java -jar /media/disk/NW-E00X_MP3_File_Manager-0.13.jar

Y ahi funciona todo.

SI hago doble click en el archivo directamente, no me reconoce la carpeta en donde esta la musica. Por lo que si o si tngo que hacer eso en consola...


Me podrían ayudar? es posible con unos simples clicks?

gracias[/COLOR]

---

### Post by Mauro22 on 2007-11-03
Ya que funciona, lo explico mejor para que no haya margen de error

1) Abrimos la consola, (supongo que estamos en /home/nombredeusuario)

Creamos un archivo vacio
```
touch nombredelscript
```
```
Ejemplo: touch Sony_e005
```

2) Lo abrimos con un editor, el que quieran, yo uso gedit
```
gedit nombredelscript
```
```
Ejemplo: gedit Sony_e005
```

3) Escribimos el script
```
 
#!/bin/sh
cd /media/disk
java -jar /media/disk/NW-E00X_MP3_File_Manager-0.13.jar
```

y lo guardan.

4) Despues lo copian a /usr/bin
```
sudo mv nombredelscript /usr/bin
```
```
Ejemplo: sudo mv Sony_e005 /usr/bin
```

5) Nos vamos a /usr/bin
```
cd /usr/bin
```
 
6) Le damos, permisos de ejecución  al script
```
sudo chmod a+x nombredelscript
```
```
Ejemplo: sudo chmod a+x Sony_e005
```

7) Vamos al escritorio (o donde quieran el lanzador)
en mi caso:
```
cd /home/mauro/Desktop
```

8) Creamos un lanzador para el script
```
ln -s ficheroalqueseapunta nombredelenlace
```
```
Ejemplo: ln -s /usr/bin/Sony_e005 SONY
```

NOTA: el script puede tener extension si quieren, es .sh, pero al agregar el "#!/bin/sh", linux ya lo sabe!
NOTA2: chmod a+x archivo. a+x significa All (Todos) + (Pueden) eXecute (Ejecutar)

Espero que quede mejor asi :)

Salu2

---

### Post by valucha on 2007-11-03
[COLOR="DarkOrchid"]mil mil mil gracias
mi mamá está eternamente agradecida

y yo ahora me voy a poner a aprender :)[/COLOR]

---

### Post by marianom on 2007-11-03
¿Funciona bien esa cosa? Hace mil años que no le meto temas nuevos a mi reproductor porque solo tengo ese "SonicStage" (sin comentarios porque me pongo violento) que anda para windows.

Comentame tu experiencia valucha, please.

Gracias.

---

### Post by Mauro22 on 2007-11-03
:popcorn:

De Nada, valucha!


Salu2

---

### Post by valucha on 2007-11-03
[COLOR="DarkOrchid"]Bueno MarianoM, paso a comentarte mi experiencia.

1ero seguí esta guia [http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html](http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html)

2do hice el script y le puse HACE CLICK AQUI 
funciona excelente.. 100% recomendable[/COLOR]

---

### Post by Mauro22 on 2007-11-04
Explicado al maximo posible,

Algunos de los capos, que lo lea, por si he cometido errores de comandos.


[SIZE=4][B]
[SOLVED][/B][/SIZE]

---

