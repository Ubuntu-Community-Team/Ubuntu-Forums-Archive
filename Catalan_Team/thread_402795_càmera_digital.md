---
title: "càmera digital"
date: 2007-04-06
forum: Catalan Team
---

### Post by emilih on 2007-04-06
Hola des de fa unes setmanes que no puc veure les fotos de la càmera digital . Pot ser una actualització del kernel a sigut la responsable. El sistema està actualitzat.

Quan intente importar les fotos ix el següent error.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Us passa el mateix?

---

### Post by emilih on 2007-04-06
He solucionat el problema de la següent forma:
En el synaptic he buscat el següents arxius : 
1r) libgphoto2-2 La versió que hi ha instal·lada és l 2.3.0. el que he fet ha sigut   paquet> força la versió> i he triat una versió anterior.
2n) libgpphoto2-2-.dev La versió instal·lada és la 2.3.0. el que he fet ha sigut el mateix que en l'apartat anterior.

Ara ja puc importar les fotos.

---

### Post by emilih on 2007-04-06
Una altra solució millor és editar l'arxiu 45-libphoto2.rules

Des d'un terminal  feu:
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

Ficar un # davant de la línia (o esborrar-la directament)
BUS!="usb*", GOTO="libgphoto2_rules_end"

Afegir a continuació 
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

Guardar 

Ara tot funcionarà correctament.

Esta solució està en els foros i sols he fet que traduir-la

Podeu veure també 

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

---

