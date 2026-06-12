---
title: "talls de conexió recurrents"
date: 2010-05-06
forum: Catalan Team
---

### Post by knuss on 2010-05-06
Hola a tothom !!

Desde que vaig actualitzar a Lucid em passa el següent:

Constantment s'em talla la conexió a la xarxa , al cap d'un moment s'em torna a conectar però es molt molest. Aproximadament cada cinc  o deu minuts.
No se si es el Network manager o que nassos li passa ,,,,
Cal dir que amb la 9.10 aixó no m'havia passat mai ,,,,

Us poso les caracteristiques de la meva maquina per si em podeu orientar una mica de com arreglar-ho.

Lucid Linx a 64 bits
Portatil Packard Bell Easy Note TJ66 
intel core dos duo a 7450
geforce gt240m
4gb de ram
Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
Intel Corporation Wireless WiFi Link 5100


Be , us dono les gracies per endavant 

Slutacions >>> Cesc

---

### Post by pelai21 on 2010-05-09
Jo tenia un problema similar. Al final vaig optar per instal·lar el wicd, i ara el wifi em funciona perfectament.

---

### Post by knuss on 2010-05-11
ospes!! investigare que es el wicd (que no en tinc n'ideia) i mirare de posar-lo.
Suposso que es un substitut del Network manager no ?

Gracies per la resposta !!

Salutacios >>> Cesc

---

### Post by knuss on 2010-05-14
hola de nou!!

Be al final he instal.lat el wicd però havía llegit que al instal.lar-lo ell sol borraba el Network. Ara els tinc tots dos.
He de borrar el network manualment ? o els he de deixar tots dos?

ospes quin embolic,,,,

Salutacions >>> Cesc

---

### Post by knuss on 2010-05-16
Hola a tothom!!

Be al final he esborrat el  Network i he deixat el Wicd , però el problema persisteix i ja no se que fer ,,,
Alguna ideia ??
Va durant força estona be però de tant en tant s'em talla la connexió i li costa un munt tornar-se a connectar.
Amb el Karmic no m'havia passat mai ,,,,,


Salutacions >> Cesc

---

### Post by CarlesOriol on 2010-05-18
A mi em passa això mateix amb amb un router wifi linksys WAG160N.

Em van comentar fa temps que podia ser culpa que no respon correctament als paquets d'un iphone.

Quin router tens? Tens algun d'aquests telèfons del dimoni?

---

### Post by knuss on 2010-05-18
ei hola!!

Doncs no el meu mòbil es dels de trucar i poca cosa mes,,,,

El router es un Zyxel 660 Hw 61 , el de la Timo ,,,,,

Es que el mes curiós es que ho fa quan li surt dels pebr**** igual esta un munt d'hores be i tot plegat comença a fallar ,,,,i quan ho fa li costa tornar a connectar-se i encara que reinicii el router i el pc li costa igual ,,,,

Misteris ,,,,,,


Salutacions >> Cesc

---

### Post by Tomàs M. on 2010-05-20
> **knuss said:**
> 
Es que el mes curiós es que ho fa quan li surt dels pebr**** igual esta un munt d'hores be i tot plegat comença a fallar ,,,,i quan ho fa li costa tornar a connectar-se i encara que reinicii el router i el pc li costa igual ,,,,



A mi em passa una cosa semblant a l'EEE, em passava amb l'encaminador antic i amb el nou, per tant aquest trasto no deu ser. I cada cop que he provat el wicd només he aconseguit empitjorar-ho.
Ja no recordo d'on ho vaig treure (segurament del launchpad), però quan comença a fer el ruc, executo aquest script (hi tinc un accés directe per a anar per feina) i en menys d'un minut, a funcionar:

```

#!/bin/bash
sudo killall NetworkManager
    sudo modprobe -r iwl4965
    sleep 2
    sudo modprobe iwl4965
    sudo NetworkManager

```

El controlador de xarxa és:

Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)


Sort!

---

