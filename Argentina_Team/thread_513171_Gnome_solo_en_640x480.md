---
title: "Gnome solo en 640x480"
date: 2007-07-30
forum: Argentina Team
---

### Post by aceki on 2007-07-30
Gente instale gnome, barbaro  anda de 10, pero solo me deja usarlo en 640x480 la placa de video es un S3 Trio de 2 Mb, cosa que con Windows uso hasta 800x600 en 16 Bit

---

### Post by lugonesjoaquin on 2007-07-30
Abre una consola y escribe:

sudo dpkg-reconfigure xserver-xorg

cuando terminas ncias el servidor grafico con Control+Alt+Backspace

---

### Post by aceki on 2007-08-08
Te cuento me instale el XFCE y tambien me paso lo mismo configure todo como vos me dijiste y no sigue en 640x480

---

### Post by facundocorradini on 2007-08-08
Probablemente el sistema esté tratando de proteger tu hard.

Fijate que entre los pasos del wizard ese tenés para elegir que resoluciones querés utilizar.
Probá tildar 800x600.

y tené cuidado con la frecuencia...

---

### Post by aceki on 2007-08-08
pero es raro, yo solo tinde 800x600 y la frecuencia es de 60 hz, probe en 70 pero nda.

Ami en windows me anda barbaro en 800x600 16bit

---

### Post by rojojuan on 2007-08-08
Me parece que falta que isntales los drives correctos para la placa. Tratá de ver si están disponibles. Probaste con  Sistema-Gestor de Controladores Restringidos?

---

### Post by aceki on 2007-08-08
y eso como lo hago?

---

### Post by aceki on 2007-08-08
Perdon, si entendi lo que dijiste, pero saque el gnome y puse XFCE y anda tambien en 640x480

---

### Post by sdm_cacto on 2007-08-08
> apt-get install xserver-xorg-video-s3 xserver-xorg-video-s3virge &&
dpkg-reconfigure xserver-xorg

 deberia solucionarlo.

Y en el wiki de xorg tenes esta info sobre que driver usas

> I have an S3 graphics card, which driver should I use ?

There are three drivers for S3 graphics chipsets:

    *      The S3 driver, which supports some of the Trio64 and older chipsets (use: Driver "s3", for details check s3),
    *      the S3 Virge driver which supports the S3 Virge and S3 Trio3D chipsets (use: Driver "s3virge", for details check s3virge),
    *      the Savage driver which supports most of the S3 Savage chipsets (use: Driver "savage", for details check "savage"]). 


---

### Post by rojojuan on 2007-08-09
> **aceki said:**
> y eso como lo hago?

Arriba de todo, tenés Apliaciones, Lugares, Sistema. Entrás por Sistema y vas a encontrar la opción de Controladores Restringidos. Fijate si e indica algún driver.

---

### Post by faktorqm on 2007-08-09
Hola, te fijaste de casualidad en tu xorg.conf, seccion screen, como te toma el monitor? sino sabes como se hace hace abri una consola y escribi:

```
sudo gedit /etc/X11/xorg.conf
```

ahi fijate en la seccion screen las frecuencias de refresco horizontal y vertical de tu monitor.

En mi casa, yo tengo una geforce 4 mx 440, y en windows la tengo (la tenia mejor dicho ;) ) en 1600x1200 y en el gnome no me la levantaba jamas a mas de 1280x1024. Tengo un monitor Samsung 997mb y en el xorg.conf me aparecia como monitor generico. Averigue cuales eran esas frecuencias, las puse en el xorg.conf, hice dpkg-reconfigure blabla y seleccione las resoluciones que queria y anduvo perfecto. Salu2!!

---

