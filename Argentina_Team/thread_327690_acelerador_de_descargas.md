---
title: "acelerador de descargas"
date: 2006-12-29
forum: Argentina Team
---

### Post by elgatogordo on 2006-12-29
**¿conocen algún acelerador de descargas que me puedan recomendar, probé con el aget pero no me baja los archivos completos**

---

### Post by felipelerena on 2006-12-30
downthmall, una extencion para firefox

---

### Post by elgatogordo on 2006-12-30
> **felipelerena said:**
> downthmall, una extencion para firefox

gracias

---

### Post by spg76 on 2006-12-30
Otro que podes probar es [Gwget]("http://gnome.org/projects/gwget/"). Está en los repositorios.

---

### Post by elgatogordo on 2006-12-30
**si , seba gracias, hice la típica de usuario de foro de ayuda, primero hago la pregunta y despues me fijo en los repositorios. bueno hasta los genios tenemos dias malos**

---

### Post by Benji86 on 2006-12-30
Freeloader es otro, tmb en los repositorios

---

### Post by spg76 on 2006-12-30
> **elgatogordo said:**
> **bueno hasta los genios tenemos dias malos**

Si, es cierto, a veces nos pasa.:)

---

### Post by elgatogordo on 2006-12-30
> **Benji86 said:**
> Freeloader es otro, tmb en los repositorios

gracias benji

---

### Post by quaid on 2006-12-30
Hablando de aceleradores... se nota la diferencia?

---

### Post by elgatogordo on 2006-12-30
> **quaid said:**
> Hablando de aceleradores... se nota la diferencia?
dame dos dias para probar y te cuento

---

### Post by Nemesis Teufel on 2006-12-30
Vale la pena si bajas muchos archivos grandes al mismo tiempo.
Primero xq podes bajar como 12 archivos, no se si mas, al mismo tiempo y ademas podes bajar sin el downthemall, osea con el gestor de descargas de FF, otros 3 o 4 archivos mas. Obvio que es al pedo casi, a menos que tengas 1 gb de banda pancha.
Con respecto a la velocidad, no es que baje mas rapido, no hace magia, solo te optimiza tu ancho de banda y la dispone de un modo para que la use totalmente, y asi tener un promedio de descarga regular y superior constante.

Si sos de bajarte 5 peliculas al mismo tiempo, viene joya!;)

---

### Post by MeduZa on 2006-12-30
> **quaid said:**
> Hablando de aceleradores... se nota la diferencia?

depende la cantidad de mirrors y que servers pero he llegado a bajar cosas 600kb por segundo constastes (picos de 630)

Saludos

---

### Post by elgatogordo on 2007-01-02
> **quaid said:**
> Hablando de aceleradores... se nota la diferencia?

si, yo estoy usando el gwget y se nota

---

### Post by Ramar on 2007-04-21
:guitar: 


Hola, soy nuevo por aca pero les traigo lo que para mì mi es uno de los mejores aceleradores de descarga:

Flashget en su ùltima versión: 1.8.1.1002, con muchos idiomas (incluido el español)
Este programa puede acelerar increiblemente la velocidad de descarga y pausarla par continuarla otro día.
Además esta nueva versión viene con la opción de bajar torrents del mismo modo que bajar un archivo corriente.

Este archivo que les traigo no se tiene que instalar, y es muy fácil de usar.
Está comprimido en winrar y así pesa 2.7 mb

Cualquier duda me avisan

Aquí le pongo el enlace

[http://www.megaupload.com/?d=A6QSPZ0S](http://www.megaupload.com/?d=A6QSPZ0S)

---

### Post by kowal on 2007-04-21
Según entiendo, **Gwget** (igual que **Kget**) es un *gestor de descargas *y no un *acelerador de descargas*.

Aceleradores de descargas en Linux pueden ser: [ProZilla](http://prozilla.genesys.ro/) (versión consola y versión GUI que se llama [ProzGUI](http://prozilla.genesys.ro/?p=prozgui).. aunque es un poco buggy),  [Axel](http://wilmer.gaast.net/main.php/axel.html) (desde consola), [doKa](http://sourceforge.net/projects/doka/) (GUI.. basado en Axel), [Aria2](http://aria2.sourceforge.net/) (desde consola), [Downthemall](https://addons.mozilla.org/es-ES/firefox/addon/201) (extensión para Firefox).

De todas formas me quedo con **Kget** que se integra perfecto a Konqueror (también a Firefox con [Flashgot](https://addons.mozilla.org/en-US/firefox/addon/220)) y al entorno KDE, que es lo que uso actualmente.

Saludos.

---

### Post by lugonesjoaquin on 2007-04-22
Hiba a responder lo mismo que Kowal..

Lo que ustedes preguntan es sobre gestores de descarga. Aparte los aceleradores de descarga no sirven! xD Por lo menos a mi nunca me sirvieron.

Otra cosa: Lo que menciona ramar. No es el FlashGet para Windows?

Yo como gestor de descargas no hay mejor cosa que el wget (Kget, gwget no son más que front end graficos de este)
Aparte hay un "truquito" para hacerlo más comodo.
Abrimos una consola:
Escribimos:
$nano descargar

Se abirá el procesador de textos nano en la consola, en el escribimos:

wget -c [http://direccionabajar//](http://direccionabajar//)

Incluso podemos meter muchos arhicos separados por un espacio. Guardamos con Control+O y salimos con Control+X.

Ahora escribimos:

$chmod +x descargar

Esto hará que el archivo de texto que creamos se vuelva un script y podamos ejecutarlo con ./descargar

Y solo comenzará wget a descargar lo que le pusiste en el archivo, y si se corta intenet o apagas la pc, no hay problema porque puedes seguirlo en cualquier momento.

Esto no es Windows che! En la consola tenemos montones de funciones!

---

### Post by lavaramano on 2007-04-23
**lugonesjoaquin**
yo hacia lo mismo con el wget de win,
armaba un batch y salia como piña, creo que es la mejor opcion.

no lo probe esto que voy a decir, pero creo que tb se podria hacer que descargar solamente sea
**wget -c $1**
entonces cuando lo ejecutas tendrias que hacer ./descarga [http://www.lala.com/cancion.ogg](http://www.lala.com/cancion.ogg) de lo contrario que te diga como se usa; lo que seria algo asi:
> 
#!/bin/bash
uso(){ echo "uso: ./descarga ARCHIVO"; }
if [ $1 = ]; then uso exit 0; else wget -c $1; fi; 


eso, sumado a un 
> 
sudo cp ~/descarga /usr/bin/descarga


seria como usar al wget, pero con la seguridad de que siempre te lo va a continuar (?)

UTILIDAD: 0
BASH SCRIPTING: 1

:lolflag:

---

### Post by lavaramano on 2007-04-23
tratando de improvizar un poco el script para que sea mas completo (?) 
salio esto (?):

> 
#!/bin/bash
uso(){ 
	echo "uso: ./descarga [-edf]" 
	echo " -e : Descarga todos los archivos con la extension ingresada de una url especifica ";
	echo " -d : Descarga recursiva de un directorio.";
	echo " -f : Descarga de un archivo."; 
}
extension () {
	echo "Ingrese la url completa (con http:// o [ftp://,](ftp://,) inclusive): ";
	echo "Ej: [http://www.pagina.com/archivos%20varios/](http://www.pagina.com/archivos%20varios/) ";
	echo -n  "> ";
	read -e URL
	echo "Ahora ingrese la extension de los archivos a bajar: ";	
	echo "Ej: ogg ";
	echo -n  "> ";
	read -e EXT
	wget -r -l1 --no-parent -A.$EXT $URL
}
directorio () {
	echo "Ingrese la url completa (con http:// o [ftp://,](ftp://,) inclusive): ";
	echo "Ej: [http://www.pagina.com/canciones/](http://www.pagina.com/canciones/) ";
	echo -n  "> ";
	read -e $URL
	wget -nc -r $URL
}
archivo () {
	echo "Ingrese la URL completa del archivo a bajar: ";
	echo "Ej: [http://www.pagina.com/cancion.ogg](http://www.pagina.com/cancion.ogg) ";
	echo -n  "> ";
	read -e ARCHIVO
	wget -c $ARCHIVO
}

if [ $1 = ]; then 
	uso 
	exit 0;
else
	if [ $1 = "-e" ]; then
		extension
	elif [ $1 = "-d" ]; then
		directorio
	elif [ $1 = "-f" ]; then
		archivo
	else
		uso
	fi
fi


se aceptan sugerencias, mejoras, lo que les parezca mejor para el scriptcito.
(nota, ya se que no soy lo mejor que hay scripteando en bash... pero es lo que hay :mrgreen:)

---

### Post by sebas.rhcp on 2007-04-23
> **Ramar said:**
> :guitar: 


Hola, soy nuevo por aca pero les traigo lo que para mì mi es uno de los mejores aceleradores de descarga:

Flashget en su ùltima versión: 1.8.1.1002, con muchos idiomas (incluido el español)
Este programa puede acelerar increiblemente la velocidad de descarga y pausarla par continuarla otro día.
Además esta nueva versión viene con la opción de bajar torrents del mismo modo que bajar un archivo corriente.

Este archivo que les traigo no se tiene que instalar, y es muy fácil de usar.
Está comprimido en winrar y así pesa 2.7 mb

Cualquier duda me avisan

Aquí le pongo el enlace

[http://www.megaupload.com/?d=A6QSPZ0S](http://www.megaupload.com/?d=A6QSPZ0S)

¿Se habrá dado cuenta que esta posteando en un foro de Linux? :-k

---

### Post by marianom on 2007-04-23
Tenés razón sebas.rhcp, estoy a milímetros de considerarlo spam.

Veamos el lado amable, fue bastante simpático, no? Además saco la bestia bashera que lavaramano ocultaba.

---

### Post by sebas.rhcp on 2007-04-23
> **marianom said:**
> Tenés razón sebas.rhcp, estoy a milímetros de considerarlo spam.

Veamos el lado amable, fue bastante simpático, no? Además saco la bestia bashera que lavaramano ocultaba.

Para mi es chino... :mad: (por ahora)

---

### Post by andy_91 on 2007-07-08
ja igual para mi prefiero los entornos graficos pero no soy tan burro como para recomendar un programa de win en un foro de linux se muy bien q programas son de win o por lo menos los mas conocidos como el nero pero hay exepciones como el mismo nero q esta disponible para ambos tipos de so lo cual no sabia hasta ayer XD

perdon si hago spam

---

