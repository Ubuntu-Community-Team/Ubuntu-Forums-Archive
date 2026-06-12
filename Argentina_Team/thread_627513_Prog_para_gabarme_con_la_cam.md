---
title: "Prog para gabarme con la cam"
date: 2007-11-30
forum: Argentina Team
---

### Post by xpelaox on 2007-11-30
Hola gente!!! Resulta que toco el bajo, y me gusta grabarme con la cam tocando y subir el videito a youtube y cosas asi. Antes hacia eso con el Windows movie maker. Que programa podria usar en Ubuntu?=D

CHAAASSS gracias xD

---

### Post by User21 on 2007-11-30
**Fijate cuál se ajusta más a tus necesidades:**

**Camorama**
 ```
sudo apt-get install camorama
```[B]
Cheese[/B]
 ```
 sudo apt-get install cheese
```

**wxCam**
Descarga el .deb de [aqui.]("http://downloads.sourceforge.net/wxcam/wxcam_0.9.6_i386.deb?modtime=1194101705&big_mirror=0")


Y cualquier **editor de video** que veas en Ubuntu, desde synaptic, tiene la opción de tomar el video de la webcam y guardarlo como archivo.
Contanos cómo te fué! :D

---

### Post by BiTFx on 2007-11-30
Acá te paso otro, que tal vez te sirva, lo encontré buscando aplicaciones, no lo he probado:
 
[[COLOR=royalblue]**Kdenlive**[/COLOR]]("http://www.kdenlive.org"), editor de vídeos libre para Linux ([http://www.kdenlive.org](http://www.kdenlive.org))
 
Wiki en Español de este programa: [http://es.wikibooks.org/wiki/Kdenlive](http://es.wikibooks.org/wiki/Kdenlive)
 
Tiene las funciones habituales de este tipo de programas, como la aplicación de efectos y transiciones, y admite multitud de formatos de entrada para las imágenes, clips o sonidos que quieras añadir. Además, podrás exportar el vídeo a los formatos más útiles, como MPEG, XviD, DV, Flash, Quicktime, etc&#8230; **Aunque está creada para KDE, en cualquier otro escritorio es bastante usable**, y seguramente lo podrás descargar desde tus repositorios habituales (paquete **kdenlive**).
 
[IMG]http://www.bitfx.com.ar/ubuntu/kdenlive.png[/IMG]

---

### Post by xpelaox on 2007-11-30
BAJANDOOO les digo desues que onda xD o les subo el videito:P

---

### Post by xpelaox on 2007-11-30
Bad News.

El camorama solo me deja sacar fotos.
El cheese cuando le pongo grabar se cierra 
y el KDENLive es para KDE, ademas ni me reconoce la cam:S

---

### Post by kowal on 2007-11-30
Con freej:

> sudo aptitude install freej
> freej /dev/video0 -s 320x240 -e captura.ogg

Con control+w empieza a grabar/deja de grabar.

Con VLC también se puede grabar de la webcam (pero no se puede ver lo que estás grabando...)

---

### Post by kowal on 2007-11-30
Acabo de probar [wxCam](http://wxcam.sourceforge.net/) (no lo conocía) y funciona de perlas. Hasta graba con sonido.

De paso agrego el link para la versión 0.9.7 [aquí](http://sourceforge.net/project/downloading.php?group_id=200261&use_mirror=ufpr&filename=wxcam_0.9.7_i386.deb&63748854)

---

### Post by sajnox on 2007-11-30
KDENLIVE esta en los repositorios de Ubuntu

```
sudo apt-get install kdenlive
```

---

### Post by User21 on 2007-12-01
Yo también probé wxCam y es la solución mas simple si solo quieres GRABAR!!! :)

---

### Post by faktorqm on 2007-12-03
hola, probe el wxcam y la verdad anda re bien, solo que pase bastante rato configurando los colores y el driver.......
no probe de grabar o sacar fotos, pero como minimo, me la muestra bien. 

Tambien probe el VLC que es un player de PM, al menos para mi. se vio todo de primera, pero no sabia ni como grabar un video ni como sacar una foto. el boton de la cam no anda, asi que ni me molesto es hacerlo andar.

despues probe mediante el aMSN y tb, andaba de primera.

Despues probe el camorama y no me acuerdo que paso, me parece que no me la reconocia y no le di bo*a :(

Sino fijate de postear la salida del comando "lsusb" si la camara es usb xD para saber que chipset tiene. salu2!!

---

