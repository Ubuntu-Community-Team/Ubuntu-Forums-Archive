---
title: "Problemes amb Gallium3D i  rv710 radeon hd 4350"
date: 2012-12-05
forum: Catalan Team
---

### Post by jmaspons on 2012-12-05
Hola,

m'he trobat amb un bug ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)) degut a que els driver privatiu fglrx no és compatible amb la nova versió d'xserver que ve amb l'ubuntu 12.10 i AMD no té previst actualitzar-lo. Els drivers lliures Gallium3D dona alguns problemes però no sé on reportar el bug. La targeta gràfica és rv710 radeon hd 4350

Sembla ser que el problema és que el sensor de temperatura (lmsensors/radeon-pci-0200/temp1) no funciona correctament i la targeta gràfica es va escalfant fins que l'ordinador queda amb la pantalla negre i no respon el teclat (Bloq Num no canvia la llumeta, Ctrl+Alt+Supr no respon...). La temperatura puja fins a 128ºC, després salta a -128º, segueix pujant fins a -50ºC i es penja.

Algun consell o lloc on puc reportar el bug?

Salut!

---

### Post by wgarcia on 2012-12-05
Jo crec que s'han d'informar contra el paquet  xserver-xorg-driver-ati . A més es pot també entrar un informe a [https://bugs.freedesktop.org](https://bugs.freedesktop.org), mira per exemple aquest:

[https://bugs.freedesktop.org/show_bug.cgi?id=37679](https://bugs.freedesktop.org/show_bug.cgi?id=37679)

El correcte és entrar l'informe aquí primer ("upstream"), després entrar l'informe a launchpad i enllaçar amb l'informe de Gnome.

---

### Post by jmaspons on 2012-12-06
Gràcies, he trobat un bug semblant i hi he afegit el meu comentari a [https://bugs.freedesktop.org/show_bug.cgi?id=27705](https://bugs.freedesktop.org/show_bug.cgi?id=27705).

Algú sap com es pot reduïr l'activitat de la targeta gràfica i evitar que s'escalfi? XRender vs OpenGL, Sistema gràfic Qt natiu vs raster...

---

### Post by wgarcia on 2012-12-06
A KDE (Kubuntu) no sé, tens alguna manera de demanar-li que no faci servir acceleració 3D, algun "fallback mode"?

---

### Post by jmaspons on 2012-12-07
Tinc les opcions que he comentat i també puc desactivar els efectes d'escriptori però tot i aixi la targeta segueix escalfant-se.

Suposo que caldrà esperar que arreglin el bug que ja porta anys al bugtracker...

---

### Post by kimet on 2012-12-07
Sospitaría que es un problema de lm-sensors i no del driver de la gràfica.
Comprovaría primer que tens els mòduls correctes dels sensors i quin programa gestiona els ventiladors i si està correctament configurat.
Si fos un problema del driver hi hauria molts reports de bugs en totes les distribucions, i almenys a mí, aquest driver (el lliure) m'ha funcionat perfectament en moltes targetes ati, no recordo exactament si el teu model concret.
Salut.

---

### Post by jmaspons on 2012-12-11
Aparentment l'únic sensor que em dona problemes és el de la targeta gràfica (valors negatius i incoherents) i els problemes han començat quan he canviat el controlador privatiu fglrx pel controlador lliure.

Alguna indicació de com puc comprovar el què suggereixes?

Si no me'n surto ja obriré un bug a l'ubuntu.

Gràcies!

---

### Post by kimet on 2012-12-11
-Queda algún rastre de fglrx? Intenta purgar tot el referent a aquest driver

-Amb la ordre **sensors** pots veure els mòduls que tens carregats i els valors que et donen.
**sensors-detect** et detecta els sensors del teu hardware i t'indica els mòduls a carregar.
pots probar a descarregar el mòdul que et dona valors extranys.

-Funcionen els ventiladors?

-Existeix l'arxiu /etc/X11/xorg.conf?
Pots probar (previa còpia) a esborrar-lo.

Més informació sobre el driver radeon:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Salut.

---

### Post by jmaspons on 2012-12-14
Hola de nou,

He intentat fer neteja de fglrx amb
```
sudo apt-get remove --purge fglrx fglRx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-radeon xserver-xorg-video-ati
```


joan@wasp0:~$ sensors
radeon-pci-0200
Adapter: PCI adapter
temp1:       -117.0°C  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +56.0°C  
Core0 Temp:   +57.0°C  
Core1 Temp:   +58.0°C  
Core1 Temp:   +54.0°C  

No se ben bé com funciona però eliminant sensors no entenc com puc solucionar el problema. Suposo que deu haver-hi una mena de termòstat que activa els ventiladors quan s'arriba a certa temperatura i si elimino el sensor no hi hauria manera de saber si cal ventilador o no.

Funcionen els ventiladors habituals però hi ha una mena de turbo (ventiladors més sorollosos que no se si són els de la targeta gràfica o no ni si són els habituals però més revolucionats) que s'engegava quan feia càlculs intensius que ara no funciona mai. Suposo que el problema bé d'aquí i ja ho he explicat a [https://bugs.freedesktop.org/show_bug.cgi?id=27705](https://bugs.freedesktop.org/show_bug.cgi?id=27705)

També he eliminat el fitxer xorg.conf i me n'ha creat un altre d'idèntic.

Segons l'enllaç que has penjat la meva targeta gràfica està suportada i funciona l'acceleració 3D... 

Alguna idea més?

Gràcies

---

### Post by kimet on 2012-12-14
Si hi ha un sensor que et marca -117° es que no funciona correctament. Si el programa que regula la velocitat dels ventiladors (fancontrol, pwconfig?) obté les dades, errònies, d'aquest sensor, no es posarà mai en funcionament i corres el risc de rostir la placa.(No sé si es el cas).
Si es un sobretaula la solució es sencilla, endollar directament els ventiladors a la font d'alimentació.

Salut.

---

