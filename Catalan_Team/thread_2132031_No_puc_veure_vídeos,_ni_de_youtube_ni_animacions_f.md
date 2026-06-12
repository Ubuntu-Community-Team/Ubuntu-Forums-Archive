---
title: "No puc veure vídeos, ni de youtube ni animacions flash, ni d'altres llocs"
date: 2013-04-03
forum: Catalan Team
---

### Post by ipelegri6 on 2013-04-03
Hola,

No recordo amb quina actualització ha passat però he deixat de veure qualsevol tipus de vídeo. He provat algunes solucions que donen a aquests fils: [http://ubuntuforums.org/showthread.php?t=1953796]("http://ubuntuforums.org/showthread.php?t=1953796") i [http://ubuntuforums.org/showthread.php?t=2104888]("http://ubuntuforums.org/showthread.php?t=2104888"), com ara desactivar l'acceleració (ho vaig haver de fer a pantalla completa perquè en pantalla petita no responia al clic del ratolí) i intentar passar a la versió HTML5 de youtube. Però res ha funcionat, ni a chromium ni a firefox, sempre em dóna un error de flash: "el connector Adobe Flash ha fallat".

La versió del connector que tinc instal·lada és la flashplugin-installer 11.2.202.275ubuntu0.12.04.1 en un ubuntu 12.04.

Alguna idea?

Irene

---

### Post by ipelegri6 on 2013-04-04
Hola de nou,

He provat de desinstal·lar el plugin, reinstal·lar-lo, fer la instal·lació manual que recomanaven a no recordo ara quin lloc (per passar un fitxer lib...so al directori de firefox-addons) i res. 
Continuo amb el problema i de fet ara estic pitjor. Fa uns dies també que chrome no funcionava, es tancava de sobte. Bé, ara es tanca de sobte al primer clic i chromium comença a fer el mateix, es tanca de sobte per exemple quan clico per mirar la configuració.

Només em queda firefox i sense vídeos :-(
Alguna recomanació? No sé per on tirar...

Irene

---

### Post by wgarcia on 2013-04-05
Abans de mirar-ho més a fons, tens un usuari "Visitant" a l'entrada del sistema? La qüestió seria provar si amb un usuari que ni sigui el teu hi ha el mateix problema. Si no fos així, el problema seria alguna cosa al teu perfil d'usuària.

---

### Post by ipelegri6 on 2013-04-08
Hola wgarcia, gràcies :-)

Ho acabo de provar i passa el mateix.

---

### Post by wgarcia on 2013-04-08
Pots mostrar l'entrada que dóna la següent comanda a una terminal:

```
lspci | grep -i vga
```

Això permetrà esbrinar quina targeta gràfica té el teu sistema.

---

### Post by ipelegri6 on 2013-04-08
Em diu que no s'ha trobat l'ordre lspci.

---

### Post by wgarcia on 2013-04-08
Suposo que ho has entrat simplement com "lspci | grep -i vga", oi? Hi havia un error en el format del meu missatge anterior.

---

### Post by ipelegri6 on 2013-04-08
:oops: No, havia entrat també [CODE]
Ara sí que ha funcionat i la resposta és:

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)

---

### Post by wgarcia on 2013-04-09
No sé si entre les coses que dius que vas provar de la pàgina on hi havia suggeriments per a aquest problema vas provar des d'una terminal:

```
sudo apt-get install --reinstall flashplugin-installer
```

---

### Post by ipelegri6 on 2013-04-09
Doncs la veritat és que no ho recordo però no em sona reinstall. Potser ho vaig provar només amb install.

Acabo de donar aquesta instrucció i encara no puc veure els vídeos tot i que sí que he aconseguit una cosa: pujar una foto a facebook. Cada vegada que ho intentava es tancava el navegador (firefox o chromium). No sé si ha estat casualitat.

Una altra cosa que em passa és que em dóna errors interns de Ubuntu 12.04. Els vaig enviant per si és útil. No puc veure els detalls perquè no es carreguen, es queda l'estrelleta central pensant (adjunto captura de pantalla).

[ATTACH=CONFIG]241155[/ATTACH]

---

### Post by wgarcia on 2013-04-09
Una altra pregunta: Vas rebent actualitzacions i les vas instal·lant sense problemes?

---

### Post by ipelegri6 on 2013-04-10
Ara sí. Vaig tenir alguns problemes però me'ls vas solucionar aquí: [http://ubuntuforums.org/showthread.php?t=2122816]("http://ubuntuforums.org/showthread.php?t=2122816")

---

### Post by wgarcia on 2013-04-10
Una cosa que em sembla que no hem provat és veure si tens els codecs (codis propietaris de mp3 etc) addicionals instal·lats, que com no són lliures Ubuntu no pot distribuir directament sinó que es mantenen en dipòsits externs. Doncs es pot veure si fas des d'una terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

i a veure si instal·la alguna cosa addicional.

---

### Post by ipelegri6 on 2013-04-10
Uf! Ha instal·lat un munt de coses!!! Et passo la informació:

S'està llegint la llista de paquets&#8230; Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet%
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  libva-x11-1 libxcb-keysyms1 linux-headers-3.2.0-29 libxcb-xv0 libtar0
  linux-headers-3.2.0-29-generic-pae libxcb-randr0 libxcb-composite0
  vlc-plugin-notify vlc-plugin-pulse libsdl-image1.2
Empreu «apt-get autoremove» per a suprimir-los.
S'insta&#320;laran els següents paquets extres:
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  libavcodec-extra-53 libavformat53 libavutil-extra-51 libfaac0
  libmjpegtools-1.9 libmp3lame0 libopencore-amrnb0 libopencore-amrwb0
  libopenjpeg2 libpostproc52 libquicktime2 libsidplay1 libswscale2
  ubuntu-restricted-addons
Paquets suggerits:
  libfaad0 sidplay-base xsidplay
Es SUPRIMIRAN els paquets següents:
  libavcodec53 libavutil51
S'insta&#320;laran els paquets NOUS següents:
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  libavcodec-extra-53 libavutil-extra-51 libfaac0 libmjpegtools-1.9
  libmp3lame0 libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libquicktime2
  libsidplay1 ubuntu-restricted-addons ubuntu-restricted-extras
S'actualitzaran els paquets següents:
  libavformat53 libpostproc52 libswscale2
3 actualitzats, 14 nous a insta&#320;lar, 2 a suprimir i 25 no actualitzats.
S'ha d'obtenir 8818 kB d'arxius.
Després d'aquesta operació s'empraran 4603 kB d'espai en disc addicional.
Voleu continuar [S/n]? s
Bai:1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/main libpostproc52 i386 4:0.8.6-0ubuntu0.12.04.1 [116 kB]
Bai:2 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/main libswscale2 i386 4:0.8.6-0ubuntu0.12.04.1 [195 kB]
Bai:3 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/main libavformat53 i386 4:0.8.6-0ubuntu0.12.04.1 [1033 kB]
Bai:4 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libmp3lame0 i386 3.99.3+repack1-1 [159 kB]
Bai:5 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/universe libopenjpeg2 i386 1.3+dfsg-4+squeeze1build0.12.04.1 [69,0 kB]
Bai:6 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/universe libavutil-extra-51 i386 4:0.8.6ubuntu0.12.04.1 [134 kB]
Bai:7 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates/universe libavcodec-extra-53 i386 4:0.8.6ubuntu0.12.04.1 [5826 kB]
Bai:8 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/multiverse libfaac0 i386 1.28-0ubuntu2 [39,5 kB]
Bai:9 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libquicktime2 i386 2:1.2.3-4build2 [346 kB]
Bai:10 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libmjpegtools-1.9 i386 1:1.9.0-0.5ubuntu7 [224 kB]
Bai:11 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/multiverse gstreamer0.10-plugins-bad-multiverse i386 0.10.21-1 [98,2 kB]
Bai:12 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libopencore-amrnb0 i386 0.1.2-1 [90,1 kB]
Bai:13 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libopencore-amrwb0 i386 0.1.2-1 [46,9 kB]
Bai:14 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe libsidplay1 i386 1.36.59-5 [73,5 kB]
Bai:15 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/universe gstreamer0.10-plugins-ugly i386 0.10.18.3-1ubuntu1 [364 kB]
Bai:16 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/multiverse ubuntu-restricted-addons i386 12 [3148 B]
Bai:17 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise/multiverse ubuntu-restricted-extras i386 57 [2840 B]
S'ha baixat 8818 kB en 34s (254 kB/s)                                          
(S'està llegint la base de dades&#8230; hi ha 247153 fitxers i directoris insta&#320;lats actualment.)
S'està preparant per a reemplaçar libpostproc52 4:0.8.5-0ubuntu0.12.04.1 (fent servir &#8230;/libpostproc52_4%3a0.8.6-0ubuntu0.12.04.1_i386.deb)&#8230;
S'està desempaquetant el reemplaçament de libpostproc52&#8230;
S'està preparant per a reemplaçar libavformat53 4:0.8.5-0ubuntu0.12.04.1 (fent servir &#8230;/libavformat53_4%3a0.8.6-0ubuntu0.12.04.1_i386.deb)&#8230;
S'està desempaquetant el reemplaçament de libavformat53&#8230;
S'està preparant per a reemplaçar libswscale2 4:0.8.5-0ubuntu0.12.04.1 (fent servir &#8230;/libswscale2_4%3a0.8.6-0ubuntu0.12.04.1_i386.deb)&#8230;
S'està desempaquetant el reemplaçament de libswscale2&#8230;
S'està seleccionant el paquet libmp3lame0 prèviament no seleccionat.
S'està desempaquetant libmp3lame0 (de &#8230;/libmp3lame0_3.99.3+repack1-1_i386.deb)&#8230;
S'està seleccionant el paquet libopenjpeg2 prèviament no seleccionat.
S'està desempaquetant libopenjpeg2 (de &#8230;/libopenjpeg2_1.3+dfsg-4+squeeze1build0.12.04.1_i386.deb)&#8230;
dpkg: libavutil51: problemes de dependències, però es desinsta&#320;larà igualment tal i com heu demanat:
 vlc-nox depèn de libavutil51 (>= 4:0.8-1~) | libavutil-extra-51 (>= 4:0.8-1~); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 gstreamer0.10-ffmpeg depèn de libavutil51 (>= 4:0.7.3-1) | libavutil-extra-51 (>= 4:0.7.3-1); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 gnash-common depèn de libavutil51 (>= 4:0.8-1~) | libavutil-extra-51 (>= 4:0.8-1~); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 libavcodec53 depèn de libavutil51 (>= 4:0.8.5-0ubuntu0.12.04.1) | libavutil-extra-51 (>= 4:0.8.5); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 libavcodec53 depèn de libavutil51 (<< 4:0.8.5-99) | libavutil-extra-51 (<< 4:0.8.5.99); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 libavcodec53 depèn de libavutil51 (>= 4:0.8.5-0ubuntu0.12.04.1) | libavutil-extra-51 (>= 4:0.8.5); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
 libavcodec53 depèn de libavutil51 (<< 4:0.8.5-99) | libavutil-extra-51 (<< 4:0.8.5.99); tot i així:
  El paquet libavutil51 serà desinsta&#320;lat.
  El paquet libavutil-extra-51 no està insta&#320;lat.
(S'està llegint la base de dades&#8230; hi ha 247162 fitxers i directoris insta&#320;lats actualment.)
S'està desinsta&#320;lant libavutil51&#8230;
S'estan processant els activadors per a libc-bin&#8230;
ldconfig deferred processing now taking place
S'està seleccionant el paquet libavutil-extra-51 prèviament no seleccionat.
(S'està llegint la base de dades&#8230; hi ha 247154 fitxers i directoris insta&#320;lats actualment.)
S'està desempaquetant libavutil-extra-51 (de &#8230;/libavutil-extra-51_4%3a0.8.6ubuntu0.12.04.1_i386.deb)&#8230;
S'està configurant libavutil-extra-51 (4:0.8.6ubuntu0.12.04.1)&#8230;
S'estan processant els activadors per a libc-bin&#8230;
ldconfig deferred processing now taking place
dpkg: libavcodec53: problemes de dependències, però es desinsta&#320;larà igualment tal i com heu demanat:
 vlc-nox depèn de libavcodec53 (>= 4:0.8-1~) | libavcodec-extra-53 (>= 4:0.8-1~); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
 gstreamer0.10-ffmpeg depèn de libavcodec53 (>= 4:0.7.3-1) | libavcodec-extra-53 (>= 4:0.7.3-1); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
 gstreamer0.10-ffmpeg depèn de libavcodec53 (<< 5:0) | libavcodec-extra-53 (<< 5:0); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
 gstreamer0.10-ffmpeg depèn de libavcodec53 (>= 4:0.7.3-1) | libavcodec-extra-53 (>= 4:0.7.3-1); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
 gstreamer0.10-ffmpeg depèn de libavcodec53 (<< 5:0) | libavcodec-extra-53 (<< 5:0); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
 gnash-common depèn de libavcodec53 (>= 4:0.8-1~) | libavcodec-extra-53 (>= 4:0.8-1~); tot i així:
  El paquet libavcodec53 serà desinsta&#320;lat.
  El paquet libavcodec-extra-53 no està insta&#320;lat.
(S'està llegint la base de dades&#8230; hi ha 247162 fitxers i directoris insta&#320;lats actualment.)
S'està desinsta&#320;lant libavcodec53&#8230;
S'estan processant els activadors per a libc-bin&#8230;
ldconfig deferred processing now taking place
S'està seleccionant el paquet libavcodec-extra-53 prèviament no seleccionat.
(S'està llegint la base de dades&#8230; hi ha 247153 fitxers i directoris insta&#320;lats actualment.)
S'està desempaquetant libavcodec-extra-53 (de &#8230;/libavcodec-extra-53_4%3a0.8.6ubuntu0.12.04.1_i386.deb)&#8230;
S'està configurant libmp3lame0 (3.99.3+repack1-1)&#8230;
S'està configurant libopenjpeg2 (1.3+dfsg-4+squeeze1build0.12.04.1)&#8230;
S'està configurant libavcodec-extra-53 (4:0.8.6ubuntu0.12.04.1)&#8230;
S'estan processant els activadors per a libc-bin&#8230;
ldconfig deferred processing now taking place
S'està seleccionant el paquet libfaac0 prèviament no seleccionat.
(S'està llegint la base de dades&#8230; hi ha 247162 fitxers i directoris insta&#320;lats actualment.)
S'està desempaquetant libfaac0 (de &#8230;/libfaac0_1.28-0ubuntu2_i386.deb)&#8230;
S'està seleccionant el paquet libquicktime2 prèviament no seleccionat.
S'està desempaquetant libquicktime2 (de &#8230;/libquicktime2_2%3a1.2.3-4build2_i386.deb)&#8230;
S'està seleccionant el paquet libmjpegtools-1.9 prèviament no seleccionat.
S'està desempaquetant libmjpegtools-1.9 (de &#8230;/libmjpegtools-1.9_1%3a1.9.0-0.5ubuntu7_i386.deb)&#8230;
S'està seleccionant el paquet gstreamer0.10-plugins-bad-multiverse prèviament no seleccionat.
S'està desempaquetant gstreamer0.10-plugins-bad-multiverse (de &#8230;/gstreamer0.10-plugins-bad-multiverse_0.10.21-1_i386.deb)&#8230;
S'està seleccionant el paquet libopencore-amrnb0 prèviament no seleccionat.
S'està desempaquetant libopencore-amrnb0 (de &#8230;/libopencore-amrnb0_0.1.2-1_i386.deb)&#8230;
S'està seleccionant el paquet libopencore-amrwb0 prèviament no seleccionat.
S'està desempaquetant libopencore-amrwb0 (de &#8230;/libopencore-amrwb0_0.1.2-1_i386.deb)&#8230;
S'està seleccionant el paquet libsidplay1 prèviament no seleccionat.
S'està desempaquetant libsidplay1 (de &#8230;/libsidplay1_1.36.59-5_i386.deb)&#8230;
S'està seleccionant el paquet gstreamer0.10-plugins-ugly prèviament no seleccionat.
S'està desempaquetant gstreamer0.10-plugins-ugly (de &#8230;/gstreamer0.10-plugins-ugly_0.10.18.3-1ubuntu1_i386.deb)&#8230;
S'està seleccionant el paquet ubuntu-restricted-addons prèviament no seleccionat.
S'està desempaquetant ubuntu-restricted-addons (de &#8230;/ubuntu-restricted-addons_12_i386.deb)&#8230;
S'està seleccionant el paquet ubuntu-restricted-extras prèviament no seleccionat.
S'està desempaquetant ubuntu-restricted-extras (de &#8230;/ubuntu-restricted-extras_57_i386.deb)&#8230;
S'està configurant libpostproc52 (4:0.8.6-0ubuntu0.12.04.1)&#8230;
S'està configurant libavformat53 (4:0.8.6-0ubuntu0.12.04.1)&#8230;
S'està configurant libswscale2 (4:0.8.6-0ubuntu0.12.04.1)&#8230;
S'està configurant libfaac0 (1.28-0ubuntu2)&#8230;
S'està configurant libquicktime2 (2:1.2.3-4build2)&#8230;
S'està configurant libmjpegtools-1.9 (1:1.9.0-0.5ubuntu7)&#8230;
S'està configurant gstreamer0.10-plugins-bad-multiverse (0.10.21-1)&#8230;
S'està configurant libopencore-amrnb0 (0.1.2-1)&#8230;
S'està configurant libopencore-amrwb0 (0.1.2-1)&#8230;
S'està configurant libsidplay1 (1.36.59-5)&#8230;
S'està configurant gstreamer0.10-plugins-ugly (0.10.18.3-1ubuntu1)&#8230;
S'està configurant ubuntu-restricted-addons (12)&#8230;
S'està configurant ubuntu-restricted-extras (57)&#8230;
S'estan processant els activadors per a libc-bin&#8230;
ldconfig deferred processing now taking place

---------------------

De moment encara no puc veure vídeos, però pot ser que hagi de reiniciar...

---

