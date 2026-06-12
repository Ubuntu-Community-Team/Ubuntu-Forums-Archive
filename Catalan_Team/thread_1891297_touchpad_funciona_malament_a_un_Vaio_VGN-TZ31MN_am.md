---
title: "touchpad funciona malament a un Vaio VGN-TZ31MN amb Ubuntu 11.10"
date: 2011-12-05
forum: Catalan Team
---

### Post by 19preguntes on 2011-12-05
Hola ubuntaires,
mai fins ara havia tingut problemes amb el touchpad, però avui, de cop, en un moment en què m'ha aparegut l'avís de que la bateria s'estava esgotant i que l'ordinador estava a punt d'hivernar, just quan hi he endollat el carregador, el touchpad ha començat a funcionar de forma molt imprecisa. Ara costa molt encertar a clicar allà on vols, avança com a batzegades, i és difícil controlar si hi estàs clicant o no (de cop és hipersensible i quasi no el pots tocar sense que cliqui allà on ets).

He mirat d'ajustar els valors d'acceleració i de sensibilitat del touchpad, però no canvia res.

També he provat la solució d'afegir una línia al grub, com s'explica en aquest enllaç (tot i que el problema no era ben bé el mateix, però ho he fet per provar a veure si hi havia sort): [http://www.ubuntizandoelplaneta.com/2010/12/touchpad-de-sony-vaio-en-ubuntu.html](http://www.ubuntizandoelplaneta.com/2010/12/touchpad-de-sony-vaio-en-ubuntu.html)
però no s'ha produit cap canvi.

Evidentment hi ha la solució de conectar un mouse usb, però ara mateix sóc de viatge, i aquí no hi tinc cap mouse (me n'hauria de comprar un).

El model del meu pc és el que he posat al títol.

Salut i moltes gràcies!

---

### Post by wgarcia on 2011-12-05
Saps si el touchpad d'aquest model de Vaio és del model "ALPS"?

---

### Post by 19preguntes on 2011-12-06
Hola wgarcia,
sembla que en efecte el model del touchpad és ALPS. No he trobat cap descripció detallada que ho digués, però en una pàgina amb drivers específics per aquest model de vaio estaven inclosos els drivers per aquesta tipus de touchpad, o sigui que dedueixo que sí.

Avui puc confirmar que el problema estar relacionat amb el fet de conectar el carregador de la bateria. Avui he tornat a treballar pel matí i el touchpad funcionava perfectament. Quan faltava poc perquè s'esgotés la bateria, l'he endollat a la corrent i a l'instant el touchpad torna a funcionar malament. He provat el què ahir no se'm va acudir: desendollar de nou el carregador, i de nou el touchpad torna a funcionar perfectamnet. Només falla quan està endollat a la corrent. No és molt estrany?

Salut i moltes gràcies per respondre!

---

### Post by BC59 on 2011-12-06
I don't understand perfectly Catalan, but a good idea to tweak the touchpad, is from Ubuntu Software Center to write gsynaptics and then you can find 2 applications about touchpad tweaking to install.

---

### Post by 19preguntes on 2011-12-06
Thanks BC59!
I did as you suggested, but nothing has changed...

---

### Post by wgarcia on 2011-12-06
Sí, es estrany. Si puguessis esbrinar exactament quin model d'ALPA tens, potser es podria fer alguna cosa més. Jo tin un touchpad ALPS en un Dell i Linux me'l reconeixia com a ratolí però no com a touchpad. Fa dos mesos van acabar un paquet que ho arregla, però no serà oficial fins la versió 12.04. La referència és:

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/550625/comments/492](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/550625/comments/492)

de totes maneres jo no instal·laria aquest paquet en el teu model, primer perquè la majoria d'ordinadors mencionats a l'informe d'error esmentat són Dells, i segon perquè et pot deixar sense resposta del touchpad si no s'instal·la bé i no és fàcil de desinstal·lar. 

Però sí que estaria bé saber exactament el model que tens. Si fas des d'una terminal:

dmesg | grep -i alps

es possible que es vegi el model.

---

### Post by BC59 on 2011-12-06
Well there is no easy way to do it...then go here and check how you can workaround this bug:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by 19preguntes on 2011-12-06
Hola wgarcia,
introduint al terminal

[CENTER]dmesg | grep -i alpsa
[/CENTER]

no em respon res. Introduint, en canvi, això:

[CENTER]dmesg | grep -i alps
[/CENTER]

em respon el següent:

[CENTER][   41.952794] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[/CENTER]

Et serveix d'alguna cosa?
Gràcies!

---

### Post by 19preguntes on 2011-12-06
Thanks again!
I will read it carefully and I hope I can solve it.

---

### Post by wgarcia on 2011-12-06
En aquest comentari:

[http://ubuntuforums.org/showpost.php?p=11461859&postcount=5](http://ubuntuforums.org/showpost.php?p=11461859&postcount=5)

diu que tenen el mateix model que tu, i que el controlador que vaig mencionar que va arreglar el meu touchpad també arregla el teu. Si el vols provar, per si un cas tingues algun ratolí preparat per poder continuar movent el cursor si la instal·lació va malament.

---

### Post by 19preguntes on 2011-12-07
Hola wgarcia,
doncs faré el què em proposes, però millor m'espero a fer-ho quan torni a casa, la setmana que ve. Ara sóc a Amsterdam, on necessito l'ordinador per la feina que estic fent, i millor no m'arrisco a provar coses de les que no estic segur, no sigui que em quedi sense ordinador!

Quan hagi provat la instal·lació que em dius tornaré a escriure per tancar aquest fil.

Gràcies per la teva ajuda.
Salut!

---

### Post by wgarcia on 2011-12-07
Molt assenyat, i que acabi bé la teva estància a Amsterdam.

---

### Post by 19preguntes on 2011-12-08
Gràcies wgarcia!

---

