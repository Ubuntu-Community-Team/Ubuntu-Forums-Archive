---
title: "Recuperar connexió network manager"
date: 2010-06-21
forum: Catalan Team
---

### Post by pserra on 2010-06-21
Hola,
ahir vaig tenir un petit 'incident' tenia el wicd i el network manager instal·lats, i no se perquè... la connexió eth1 no em connectava... solsament la wifi.
Fent proves de descartar incompatibilitats entre els 2 programes... no se com va anar que se'm van desinstal·lar els 2....
VAig estar mirant... de baixar-me els pàquets i instal·lar-los, però al fer la instal·lacio requereix connexió per baixar un paquet que falta i em 'peten' les instal·lacions, tant de un com de l'altre....
També vaig estar mirant des de el live aquest enllaç:
> sudo su
mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
apt-get update
apt-get upgrade
apt-get install network-manager network-manager-gnome

Ctrl+D para salir de chroot.
      
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev
umount /mnt
reboot

però al fer els updates s'esta 10 minuts baixant arxius i em peta per manca de capacitat a mnt....

alguna suggerencia?
quin programa considereu 'millor' el wicd o el manager?
a mi m'agrada el manager ja que si de vegades em falla la connexio (la meva compañia de moment no em dona servei gaire ok)puc visualitzar si hi ha alguna wifi 'oberta'.. mentre que el wicd no ho tinc....

---

### Post by akyra on 2010-06-21
Has probat a anar a: (Sistema > Administarcion > Red) i podràs accedir a les diferents interficies de xarxa. Jo agafaria la de cable, i si tens els repositoris correctes tornaria a instal·lar el "network-manager".
Sino també ho podràs fer amb el disc d'instal·lació d'ubuntu seleccionat-lo en els "origens del software", potser és l'opció més senzilla.

Jo he probat tots dos i trobaràs opinions per tots els casos, però finalment sempre m'he quedat amb el "network-manager". En el meu cas el Wicd no soportava WAP2.

Salutacions.

---

### Post by pserra on 2010-06-21
> **akyra said:**
> Has probat a anar a: (Sistema > Administarcion > Red) i podràs accedir a les diferents interficies de xarxa. Jo agafaria la de cable, i si tens els repositoris correctes tornaria a instal·lar el "network-manager".
Sino també ho podràs fer amb el disc d'instal·lació d'ubuntu seleccionat-lo en els "origens del software", potser és l'opció més senzilla.

Jo he probat tots dos i trobaràs opinions per tots els casos, però finalment sempre m'he quedat amb el "network-manager". En el meu cas el Wicd no soportava WAP2.

Salutacions.

merci AKYRA,
si vaig a administració -->eines de xarxa em surt el wifi i el eth1... però no visualitzo opció de reinstal·lar rés..
Ahir amb el Live CD vaig estar mirant com baixar el rentwork manager e instal·lar-lo al disc dur, però no hi va haver manera...  des de el live cd tant sinaptic o terminal per defecte treballa virtual.... com ho puc fer per fer canvis al meu ubuntu??

Merci

---

### Post by tanreb20 on 2010-06-21
El tema és no iniciar amb el LiveCD, sino amb el teu ubuntu normal, i a fonts d eprogramari marcaar la opció del CD com a origen de software.

---

### Post by pserra on 2010-06-21
> **tanreb20 said:**
> El tema és no iniciar amb el LiveCD, sino amb el teu ubuntu normal, i a fonts d eprogramari marcaar la opció del CD com a origen de software.
disculpeu, estic peix amb el tema... ho he seleccionat, he introduit el live cd al lector.... però des de  el Synaptic em surt error de que no es pot connectar...
Que faig malament??
Merci.

---

### Post by akyra on 2010-06-22
A veure si ho poc mirar a la nit el tema del CD, però si tens el eth1 i connectes el cable no et funciona internet?

---

### Post by tanreb20 on 2010-06-22
En cas qeu al cnectar el cable eth1 no t'agafi conexio fés aixó:

```
$ dhclient
```

I t'agafará IP del router, aixi podrás navegar i descarregar el programa que prefreixis (que per mi és el NM)

---

### Post by pserra on 2010-06-22
> **tanreb20 said:**
> En cas qeu al cnectar el cable eth1 no t'agafi conexio fés aixó:

```
$ dhclient
```

I t'agafará IP del router, aixi podrás navegar i descarregar el programa que prefreixis (que per mi és el NM)

MEEERCI TANREB...
mira que ha sigut fàcil... unicament he hagut d'afegir els sudo... ok merci

---

