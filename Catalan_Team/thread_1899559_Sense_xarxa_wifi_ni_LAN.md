---
title: "Sense xarxa wifi ni LAN"
date: 2011-12-23
forum: Catalan Team
---

### Post by tocapelfoc on 2011-12-23
Hola!

Bona nit a tothom! Sóc nou per aquí, i espero poder contribuir a fer més gran aquesta comunitat! De moment, però, començo amb un marronet que tinc.

M'he comprat un ordinador nou i hi he instal·lat l'Ubuntu 11.10. El cas és que tot és correcte menys una cosa importantíssima: no tinc connexió ni de wifi ni de LAN. És a dir, quan vull triar a quina xarxa connectar-me, no me'n surt cap.

Ara estic escrivint amb el portàtil, just al costat de l'ordinador nou. És realment molest, perquè no puc fer cap consulta amb la nova màquina, i no sé si és un problema de drivers o de vés a saber què...

Us deixo la informació que (pel poc que sé) potser necessiteu per fer-me un cop de mà.

Fent un ***lspci*** em surt, entre altres coses:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

Fent un ***iwconfig***:

lo        no wireless extensions
eth0       no wireless extensions


Estic una mica desesperat, perquè necessito l'ordinador per treballar, i veig que això no sé pas com solucionar-ho...

A veure si em podeu ajudar!
Moltíssimes gràcies a tots!!

---

### Post by wgarcia on 2011-12-24
Sembla que és un problema amb aquesta tarja de xarxa i que s'està produint a moltes distribucions de Linux (Fedora, Ubuntu, etc.). Al següent article donen una solució:

[http://forums.linuxmint.com/viewtopic.php?f=49&t=80757](http://forums.linuxmint.com/viewtopic.php?f=49&t=80757)

Si tens dificultats seguint les instruccions per manca d'experiència de treballar amb la terminal de comandes o comprensió de l'anglès, comenta-les aquí.

---

### Post by tocapelfoc on 2011-12-26
De moment ho he solucionat posant el mòdem al costat de l¡ordinador de sobretaula. Com que és una torre i no s'ha de moure d'aquí, ja em detecta internet per cable, així que no em preocupa gaire que no detecti la wifi.

Gràcies!

---

### Post by CarlesOriol on 2011-12-26
Encara que no soc partidari d'aquesta solució: Has provat amb el ndiswrapper?

---

