---
title: "ejecutar archivo"
date: 2007-11-14
forum: Argentina Team
---

### Post by lordpuppet on 2007-11-14
Buenas,

baje, descomprimí y configuré el EPSXE, el emulador de playstation 1 en su versión para linux siguiendo un tutorial simple. El problema viene cuando quiero ejecutar EPSXE, segun el tuto, hay que hacer:

"./epsxe"

EL archvio "epsxe" existe y esta en la carpeta donde tengo el programa, pero no tiene extension y si le doy doble click no pasa nada, pero wine intenta abrirlo, pues en la configuración, "abrir con..." dice wine emulator.

Sin embargo cuando hago ./epsxe sobre la carpeta donde esta este archivo no abre nada :S 

esteban@esteban-desktop:/usr/local/games/epsxe$ ./epsxe
esteban@esteban-desktop:/usr/local/games/epsxe$ 

Pero no se muestra nada. Como puedo ejecutarlo alternativamente?

---

### Post by por100pre1 on 2007-11-14
Trata esto:

```
cd /usr/local/games/epsxe
```

```
sudo chmod a+x epsxe
```

```
./epsxe
```

Hazme saber si te funciona. :-k

---

### Post by lordpuppet on 2007-11-14
No, sucede lo mismo, nada.

---

### Post by por100pre1 on 2007-11-14
> **lordpuppet said:**
> No, sucede lo mismo, nada.

¿Y que tal asi? Si es un instalador prueba esto:

```
sudo su -c './epsxe'
```

Si no es un instalador hazme saber...
[B]
Muestrame el enlace al tutorial...[/B]

EDIT: [Lee este tutorial]("http://ubuntuforums.org/showthread.php?t=612021").

---

### Post by lordpuppet on 2007-11-14
No funciona, no es un instalador, es el ejecutable del programa, simplemente basta descomprimir el zip que esta en la pagina del emulador.

El tutorial que segui es este
[http://www.ubuntu-es.org/index.php?q=node/11348](http://www.ubuntu-es.org/index.php?q=node/11348)

---

### Post by por100pre1 on 2007-11-14
> **lordpuppet said:**
> No funciona, no es un instalador, es el ejecutable del programa, simplemente basta descomprimir el zip que esta en la pagina del emulador.

El tutorial que segui es este
[http://www.ubuntu-es.org/index.php?q=node/11348](http://www.ubuntu-es.org/index.php?q=node/11348)

En este momento no puedo cargar la página. Los DNS de mi ISP no están trabajando bien aquí. ¿Haz probado PCSX? Está en los repositorios.

```
sudo aptitude install pcsx
```

**EDIT: Ya pude mirar la pagina. Prueba verificar los permisos de las carpetas. ¡Tremendo testamento de guía! De solo mirar tantos permisos distintos para tantas carpetas ya me da dolor de cabeza.**

---

### Post by lordpuppet on 2007-11-14
El tutorial que me pasaste es muy parecido al que segui yo, pero lo hice como decía en el link que pusiste e hice todo satisfactoriamente, sim embargo, cuando termine, me paso lo mismo de siempre
 
Lo ejecuto y no anda. 
EL tuto que me pasaste hace un script para ejecutarlo al escribir "epsxe" en la consola de una, sin embargo es evidente que el problema es exactamente el mismo de siempre.

---

### Post by por100pre1 on 2007-11-14
No se me ocurre nada más aquí. Asumo que descargaste todo incluso el BIOS. Veamos si alguno de los muchachos aquí te dan mas luz al respecto.

---

### Post by lordpuppet on 2007-11-14
Si, el bios lo tengo, de igual modo debería arrancar el emulador independientemente de este (lo he usado en windows)

Bien, esperaré a ver si alguien me ayuda con este unsolver mystery

La verdad es que no quiero ir a windows para emular mis juegos, llegue al punto de tener un ubuntu tan perfecto que tengo total aversión por el windows xp de mi hermano :P

---

### Post by lordpuppet on 2007-11-15
Encontré la solución al escribir un post similar en el foro de begginers, posteo la solución por si alguien se topa con este post buscando como loco:

Simplemente hay que instalar el upx-ucl pues el archvio "epsxe" esta comprimido:

```
sudo apt-get install upx-ucl
```

Despues nos situamos donde esta el archivo epsxe y hacemos

```
upx -d epsxe
```


Y para correrlo:

```
./epsxe
```


Esto es todo.

---

### Post by por100pre1 on 2007-11-16
¡Magnífico! Me alegra que hayas resuelto tu problema. :)

---

