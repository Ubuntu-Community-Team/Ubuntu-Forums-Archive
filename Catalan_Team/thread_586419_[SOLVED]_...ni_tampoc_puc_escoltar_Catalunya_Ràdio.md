---
title: "[SOLVED] ...ni tampoc puc escoltar Catalunya Ràdio."
date: 2007-10-22
forum: Catalan Team
---

### Post by lo gambusí on 2007-10-22
ni icat FM, ràdio bronka, ràdio contrabanda...ni la COPE!! xD

En lo cas de Cat Ràdio, per exemple: 

[http://www.catradio.cat/reproductor/audio.htm?ID=CATRADIO](http://www.catradio.cat/reproductor/audio.htm?ID=CATRADIO)

Diu: si vas amb Linux prem a tal lloc. Premo, se m'obri el reproductor i se queda penjat.:(

---

### Post by jerec on 2007-10-22
Si tens instal·lat el mplayer i el mozilla-mplayer hauries de poder escoltar la radio triant l'opció "Windows Media Player" (fixat si a sota de cada opcio posa Instal.lat de color verd)

Per poder reproduir media streaming (RTSP - QuickTime Real-Time Streaming Protocol File) tal i com he dit has de tenir genial mplayer o algun altre client tal com el realplayer.

Per instalar-los, el mplayer tira de dpkg o de synaptic
Per el realplayer l'has de descarregar d'aqui: [https://player.helixcommunity.org/downloads/]("https://player.helixcommunity.org/downloads/")
escull el RealPlayer 10.0.9 Gold i triar la versio Installer.
una vegada al teu disc dur li poses permisos d'execucio:
# chmod 755 realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
i l'executes, segint les instruccions d'instalació
# sudo ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

Ara prepara el firefox per streaming media
a la barra d'adreçes posa about:config
a sobre de la pagina amb els valors boto dret i "NEW --> STRING" posant-li de nom network.protocol-handler.app.rtsp
valor del programa, el que vulguis /usr/bin/realplay o /usr/bin/gmplayer (posa-hi el gui que sino t'el executara en background)

hi ha una prova pilot [http://www.catradio.cat/pilotcatradio/]("http://www.catradio.cat/pilotcatradio/")
on es pot escoltar en format mp3 o ogg

De totes maneres l'adreça que passen entremitg del la runa de flash amb el enllaç de linux no funciona, pero aixo et servira per altres llocs.

---

### Post by nickpage on 2007-10-22
Jo normalment escolto RAC1, i ho faig amb una aplicació que es diu StreamTuner, funciona molt be.

---

### Post by lo gambusí on 2007-10-22
Quan vaig a obrir l'mplayer me diu:

No application suitable for automatic installation is available for handling this kind of file.

D'altra banda... nickpage, he baixat lo programa este, com ho faig per posar, per exemple, RAC1 com fas tu? 

Gràcies als dos.:)

---

### Post by nickpage on 2007-10-22
Per escoltar RAC1 has de fer el següent,

vas a la pestanya on posa Shoutcast, fas una busqueda ficant RAC1, et sortira RAC i RAC105 o alguna cosa així. Simplement fas doble click i se't posarà en marxa.

De tota manera has de tenir el xmms instal·lat com a reproductor

---

### Post by cortsenc on 2007-10-22
Estic escoltant **Contra Banda** obrint el **Rhythmbox** i amb el botó dret sobre ràdio posar "*Emisora de ràdio per internet nova*" enganxa aquesta direcció que et proporciona la seva web:
 [http://porticoluna.org:8000/contrabanda](http://porticoluna.org:8000/contrabanda)

I per escoltar **Ràdio Bronka**, afegeix aquesta direcció de la mateixa manera que abans:
[http://giss.tv:8000/rbronka.ogg](http://giss.tv:8000/rbronka.ogg)

---

### Post by lo gambusí on 2007-10-22
Res ;(

A lo de l'streamtuner este me diu No s'ha pogut executar el procés fill «xmms» (no such file or directory).

I lo rythmbox se'm queda penjat...

---

### Post by patrickfromspain on 2007-10-22
insta&#322;lat el totem-mozilla. Clickant els 2 enllaços que heu posat (radio bronka i contra banda) se m'obre una altra pestanya i ho puc escoltar perfectament. Icatfm tambe hem funciona.

---

### Post by lo gambusí on 2007-10-22
Ja ho tinc instal·lat, i igual... :s

---

### Post by marcoil on 2007-10-22
El reproductor basat en flash que empren a les emisores de la generalitat no funciona gaire bé amb Linux, però hi ha una altra manera d'escoltar-les.

Basta anar al mapa de la web que hi ha a cada emisora i elegir, enlloc de "Directe", l'enllaç WM o MPEG4.

A jo el de WM me funciona perfecte, m'obri el reproductor de pel·lícules i se sent perfectament, molt millor que emprant l'mplayer per fer funcionar el reproductor en flash.

L'enllaç directe per escoltar Catalunya Ràdio és aquest:
[http://www.catradio.cat/directes/catradio_wm.m3u](http://www.catradio.cat/directes/catradio_wm.m3u)

Esper que us funcioni!

---

### Post by lo gambusí on 2007-10-23
Vaja, ara sí que me funciona.:)

Molt bé, aniré buscant los diferents enllaços.

Moltes gràcies! :)

---

