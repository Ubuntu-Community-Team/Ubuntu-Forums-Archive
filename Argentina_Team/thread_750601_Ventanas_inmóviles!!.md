---
title: "Ventanas inmóviles!!"
date: 2008-04-09
forum: Argentina Team
---

### Post by wanchan on 2008-04-09
Hola el problema es que cada ventana que abro no la pudo redimencionar ni moverla, tengo instalado linux 7.10 gutsy con compiz-fusion, no se si se debe a la configuración de compiz. Pero antes no me sucedia esto. Las ventanas se ven sin el marco arriba de la barra de tareas y por eso no puedo moverlas y cambiar su tamaño.

Si alguien puede postear que opciones tengo que habilitar del compiz estaria agradecido.
Gracias!!

---

### Post by kha0s101 on 2008-04-09
[COLOR="DarkGreen"]Hola. 

Estás en lo correcto, es config de Compiz. En la sección _Window Management_ debés tildar **Mover ventana**. Eso sería todo.

Espero que te sirva.

Saludos.[/COLOR]

---

### Post by guisheca on 2008-04-09
Ese es un problema del decorador de ventanas emerald, y es bastante conocido.
Buscá información sobre problemas con el decorador de ventanas, no es que no te quiera ayudar, pero es lo más rápido, porque puede ser por varias razones que tenés el problema ese. Pero en todos los casos es fácil solucionarlo.
Un saludo

---

### Post by mauriciog on 2008-04-09
wanchan:
Quizas esto pueda ayudarte: [http://www.ubuntu-es.org/index.php?q=node/69109](http://www.ubuntu-es.org/index.php?q=node/69109)
Saludos!

---

### Post by wanchan on 2008-04-09
Gracias por responder a todos, he estado buscando y me tope con esta web [http://www.ubuntu-es.org/index.php?q=node/57256]("http://www.ubuntu-es.org/index.php?q=node/57256")
pero es para beryl, pero igual segui los pasos de la primera solucion y no paso nada. La segunda solucion no me hace falta porque me fije en el archivo xorg.conf y no hice las modificaciones en las secciones del archivo que decia que hiciera, porque ya tenia los parametros que me indicaba cambiar. 
Alguna otra solucion?

---

### Post by oktubrer on 2008-04-10
En la configuración de Compiz además de "mover ventanas" como te dijeron antes también aparece "redimensionar ventanas" que lógicamente tendría que estar tildado.
Fijate si aparece tildado "decoración de ventanas" que es lo que agregaría la barra de título y borde que dijiste que no estaban.

Todo lo anterior solamente si tenés instalado el  compizconfig, sino para instalarlo:
```
sudo aptitude install compizconfig-settings-manager
```

Si usas Emerald podés también levantarlo en consola, cuando lo había instalado en Xubuntu se me caía todo el tiempo y lo levantaba así:```
compiz --replace -c emerald
```

Pero no es una solución definitiva si se cae seguido.  A mi me empezó a funcionar sin problemas cuando actualicé a Gutsy.

---

### Post by User21 on 2008-04-10
Yo sigo creyendo que falta activar los plug ins de Compiz de Mover Ventana y  Redimensionar , que estan en el compizconfig-settings-manager !
En consola solo tipea ccsm y busca el apartado donde se manejan las ventanas.

---

### Post by wanchan on 2008-04-10
Me fije si en la configuracion de compiz estaban tildadas las opciones de "Mover ventana" y "Combiar tamanio de ventana" y estan tildadas; pero sigo sin redimensionar las ventanas y no aparece en ninguna la barra de titulo.
Como puedo saber que decorador de ventana utilizo, emerald o el que esta por defecto? Hay algun comando que me diga?

---

### Post by pante on 2008-04-10
¿Las ventanas aparecen como pegadas a la parte superior de la pantalla?

Hace tiempo yo usaba Fluxbuntu y se rompió (creo recordar) el gestor de ventanas. Y las ventanas aparecían sin bordes, inmóviles, no las podía redimensionar, etcétera. 

Saludos :)

---

### Post by wanchan on 2008-04-10
No se si pegadas, va dan esa sensacion si los bordes de dos ventanas tienen el mismo color, en mi caso son de color gris claro.
La unica forma de moverlas es clickear alt+F7, un embole...
La verdad no se cual es el problema, y esto me sucedio de un dia para el otro.

---

### Post by oktubrer on 2008-04-11
Estuve haciendo algunas pruebas.  Si no funcionó con el emerald, probá con esto:

```
compiz --replace gtk-window-decorator
```

que es el que viene por default en Gutsy

Si no funciona posteá las salidas de las pruebas que hayas hecho en la terminal con estos comandos.

---

### Post by wanchan on 2008-04-12
Bueno no se porque no puedo poner una imagen de la captura que hice de los comandos, en la opcion "Insert image", puse la URL pero me escribio esa misma URL y no la imagen.
Por lo que voy a escribir la salida, menos mal que no es larga:)

$ compiz --replace -c emerald
Cheking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Cheking for texture_from_pixmap: present.
Cheking for non power of two support: present.
Cheking for Composite extension: present.
Comparing resolution (1024x768) to maximun 3D texture size (4096): Passed.
Cheking for nVidia: present.
Cheking for FBConfig: present.
Cheking for Xgl: not present.
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: feedesktop
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: fusioncap.png

/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: compizcap.png 
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: fusioncap.png
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: compizcap.png 

Me canse de escribir, para el otro comando me sale casi la misma salida, si alguno me puede decir como hago para pegar la imagen aqui se lo agradeceria de todo corazon.

Pero ninguna de los dos comandos funciona. Es mas el 2do. me hizo reiniciar la maquina.

---

### Post by wanchan on 2008-04-13
Bueno instale emerald, pero no veo alguna opcion para cambiar o modificar o activar barras de titulos. probe de nuevo los comandos que me dijeron en los anteriores post y no se arreglo el problema.
La verdad me tiene un poco las bolas inchadas, me parece que tendria que reinstalar compiz de nuevo, perece que es probleme de el. O que solucion me recomiendan?

---

### Post by oktubrer on 2008-04-13
Honestamente me superó, teniendo en cuenta que las posibilidades que te di no funcionaron voy a dejar que conteste alguien más experimentado asi también aprendo.

---

### Post by Mister X on 2008-04-14
Una prueba que podes hacer para tratar de aislar el error es ingresar a gnome con un usuario nuevo, con el escritorio estandar, de esta manera vas a saber si el error es solo de la configuracion de tu usuario. 
En el caso que funcione sin problemas, lo que podes hacer es reproducir en el usuario nuevo la configuracion que tenes en tu usuario, por ejemplo copiando la carpeta de configuracion de compiz, etc.

---

### Post by wanchan on 2008-04-15
OK lo voy a probar y posteo como me fué. Con escritorio estandar te referís con efectos normales? sin compiz? El archivo de configuración de copiz en que directorio está?

---

### Post by Mister X on 2008-04-15
la configuracion de compiz es manejada por gconf y esta en ~/.gconf/apps/compiz

acordate que si la copias desde tu usuario al usuario de prueba, vas a tener que cambiarle el propietario a la carpeta y todo su contenido

---

### Post by wanchan on 2008-04-15
El propietario lo cambio con chmod? y como que tengo que cambiar el contenido del archivo compiz?

---

### Post by oktubrer on 2008-04-15
El propietario se cambia con chown.
Lo que quiso decir es que le tenes que cambiar el propietario a todo el contenido de la carpeta tambien.

---

### Post by Mister X on 2008-04-16
A ver, supongamos que el usuario de prueba se llama <prueba>

```

sudo chown -R prueba:prueba /home/prueba/.gconf/apps/compiz/

```

---

