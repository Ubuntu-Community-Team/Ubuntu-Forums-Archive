---
title: "[SOLVED] No puc escoltar so al Ubuntu 7.10"
date: 2007-11-10
forum: Catalan Team
---

### Post by carlesbm on 2007-11-10
Hola  altre cop

     Be vaig pulint els problemes que hem van sorgint, hem trobo no puc escoltar cap so, pels altaveus, fins ara no havia fet gaire cas de aquesta incidencia peò ara voldria escoltar algun programa de readio i algun video i no puc.

    La tarja de so es integrada dins la placa Base Asus model P5B

Us adjunto el que apareix algestor de dispositius

Tamb eus adjunto la configuracio de SO

---

### Post by papapep on 2007-11-10
Ens hauries de dir quin xipset de so tens, Carles.

Fes:

```
lspci | grep audio
```

i enganxa el resultat.

UPS, ara he vist les impresions de pantalla.

Fes:

```
aplay -l
```

i enganxa la resposta.

---

### Post by carlesbm on 2007-11-10
Hola Josep
    i gracies per la teva ajuda

Aquest es el resultat  no aparwix res

el sesultat de la segona instruccio es:

carles@carles-Despatx:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
carles@carles-Despatx:~$

---

### Post by papapep on 2007-11-10
No pateixis, si no és una placa PCI com tu bé has dit, no tenia sentit la ordre que t'he dit primer.

Ara mira a veure si tens el dimoni del so funcionant:

```
ps -e|grep esd
```

---

### Post by carlesbm on 2007-11-10
Crec que no  hi es

carles@carles-Despatx:~$ ps -e|grep esd
carles@carles-Despatx:~$ 

mmmm..... Complicat?

---

### Post by papapep on 2007-11-10
Bé, més que complicat curiós :-)

I si crides l'alsamixer, surt?

```
alsamixer
```

---

### Post by carlesbm on 2007-11-10
Apareix aixó.

---

### Post by CarlesOriol on 2007-11-10
Tira cap a la dreta no fos cas que sols tinguessis activada la sortida digital.

---

### Post by carlesbm on 2007-11-10
perdoneu no havia vist que segui mes a la dreta

aqui teniu la imatge completa

---

### Post by CarlesOriol on 2007-11-10
Anem per parts.

Has comprovat que:

1 - Els altaveus funcionen i tenen volum. - Si toques la punta del connector fa un sorollet

2 - Els altaveus estan connectats al seu lloc. - Connector verd de la placa base
      No estan connectats a cap altre dispositiu
  
3 - Quan obrim el gnome-volume-control (ho sento però no soc tant de terminal com en patatet) tenim els volums activats. Per a tots els dispositius de so ( fitxer > canvia de dispositiu ) . 

4 - Fes també una repasada ràpida a edita > preferències selecciona-ho tot i mira-ho.

5 - No hi ha cap programa que estigui bloquejant el so. - En feisty a vegades determinats programes en flash em deixaven sense so.

6 - Prova al selector de sistemes multimedia ( gstreamer-properties ) diverses configuracions.

(els primers punts encara que sembli de parvulari comprova'ls bé)

---

### Post by carlesbm on 2007-11-10
Be ja esta solucionat, resulta que aqui el menda no havia conecta correctament el jack del altaveus.


Gracies ha tots

---

