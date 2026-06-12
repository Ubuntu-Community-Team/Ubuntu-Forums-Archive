---
title: "Beryl i problemes amb videos"
date: 2007-05-27
forum: Catalan Team
---

### Post by ernestux on 2007-05-27
Hola,

Seguint les instruccions perfectes de l'Orestesmas en aquest forum he aconseguit fer córrer el BERYL , i amb la targeta de so Intel 945 del portàtil.  Ara m'he trobat el problema que he intentat veure videos (vlc, reproductor videos.....) en format .mov , ogg-theora , .avi i no es veu la imatge -o amb salts- tot i que el so correr bé.  Aleshores si des de beryl selecciono el gestor de finestres  METACITY en comptes de BERYL sí que veig videos correctament. 

Com s'hauria de fer per tenir l'entorn  BERYL i poder veure videos ?

Gràcies
Ernest

---

### Post by CarlesOriol on 2007-05-27
Canvia a /home/usuari/.gnome2/totem_config

video.driver:auto

prova xv o x11 o opengl... (pots instal·lar el xine i veure les opcions)

---

### Post by ernestux on 2007-05-27
Hola Carles,

En el  /home/usuari/.gnome2/totem_config  ho tinc tot comentat (#és normal?), i també:

# video driver to use
# string, default: auto
#video.driver:auto

Com que soc bastant ignorant què hauria de fer? ,  canviar  auto per xv, x11 ... i descomentar

Jo uso sobretot vlc, i en l'arxiu /home/usuari/.vlc/vlcr  també està tot comentat .
xine no el tinc instal·lat i  mplayer no el control·lo.

Gràcies i Bona nit

---

### Post by CarlesOriol on 2007-05-27
Més fàcil encara:

executa gstreamer-properties i la penstanya de video canvia els diferents modes a connector

(el # vol dir que la opció està predeterminada i # serveix comentar la linia. Si fas canvis cal que treguis el #.)

---

### Post by ernestux on 2007-05-28
Hola,

He provat de canviar el gstreamer-propietats i marcant x11 o xv  no m'ha funcionat.
Després hebuscat pel google i he trobat una solució que m'ha funcionat.

en vlc :  paràmetres/preferències/videos/mòduls de sortida/  
clico: opcions avançades i "Sortida de vídeo X11"

Això només és pel reproductor vlc, és clar; que crec que no usa gstreamer especificament (no?). 
 Amb cada reproductor s'hauria de fer quelcom semblant, però en el reproductor de pelis per defecte de l'ubuntu , no trobo el mateix i em diu: 
Us cal el connector video/x-gst-fourcc-dmb1 decoder per reproduir aquesta pel·lícula, però actualment no el teniu instal·lat.

Ernest

---

### Post by josep314 on 2007-05-28
Hola !

Val la pena actualitzar a ubuntu 7.04, desde la verssió 6.

---

### Post by ernestux on 2007-05-28
Hola josep314,

Jo  tinc  el 7.14 feisty , ja ! .  No sé quines configuracions tinc, perquè tampoc és plan limitar-te  treballar amb vlc,o haver de canviar cada cop el Gestor de finestres.
Acabo de comprobar que amb MPLAYER ,  posant sortida x11 o xv , també  funciona bé.   Menys mal !

Ernest

---

### Post by crazyserver on 2007-05-29
Hola Ernestux!

Veig que tens els maiteixos problemes que jo, jo només faig servir Totem, i tot és problema del xv, si uses video sense xv funciona bé i si no no funciona (encara que de vegades si), la meva solució és canviar de gestor ja que prefereixo tenir el xv activat (sempre es veu millor). L'xv s'ha de configurar per cada tipus de codec d'audio-video.

Pots provar també canviant entre drivers privatius i lliures, jo tinc una ati i amb els lliures amb passa i amb els privatius no em funciona el beyl directament... però tinc entés que per les nvidia ja esta solucionat el problema pels privatius i pels lliures no se com funciona la cosa... Tot és anar provant (drivers, gestor i xv)

---

