---
title: "Virtualbox  vs  USB"
date: 2009-07-11
forum: Catalan Team
---

### Post by lFossil on 2009-07-11
Hola bones estic intentant fer que funcionin els usb amb la virtualbox mitjançant [aquest fil]("http://blogdenfaktor.blogspot.com/2008/07/ports-usb-en-virtualbox-i-hardy-heron.html") però al principi on diu:




[I]Editar el fitxer mountdevsubfs.sh (sudo gedit /etc/init.d/mountdevsubfs.sh) i

Canviar això:[/I]
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb



*Per:*

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb




Tinc el problema que el primer paràgraf que diu que hi hem de trobar no el tinc i per tant no puc continuar amb la instal·lació, alguna idea nois?

---

### Post by oriolsbd on 2009-07-11
Si et fixes, en el fitxer mountdevsubfs.sh, hi ha una línia que hi posa:
```
do_start () {
```
Unes línies més avall, es tanca la clau que s'ha obert aquí. Jo ho he posat en les línies just abans de tancar la clau.

Salut!

---

### Post by dafaktor on 2009-07-12
Salut company,

el fil del què parles és del meu bloc i funcionava perfectament amb les versions anteriors.

Amb les últimes versions no cal fer res per a què et funcioni; si de cas, l'únic que has de comprovar és que el teu usuari pertany també al grup *vboxusers*.

Au !

---

