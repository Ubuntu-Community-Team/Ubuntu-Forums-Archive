---
title: "Usb 2.0 (MTP/UMS)"
date: 2007-11-21
forum: Catalan Team
---

### Post by farigola on 2007-11-21
Hola,
El passat dissabte vaig comprar un reproductor Mp3 Samsung T10 aquest aparell utilitza un sistema de connexió USB (mtp/ums). Al connectar aquest al meu equip l'aparell reconeix USB i comença a carregar la bateria, però no s'obre cap pantalla per veure el seu contingut, es a dir l'estructura de carpetes. He fet un reset al aparell T10 per si calia, però no ha funcionat. Des de konqueror i executant Suports d'emmagatzematge només surt el disc dur de l'ordinador
Sabeu si cal fer alguna operació especial per poder veure el contingut?

Equip amd64 athlon x2
kubuntu 7.10

---

### Post by farigola on 2007-11-21
Perdoneu per no haver anotat les proves 
execució de lsusb
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 010: ID 04e8:508a Samsung Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000

dmesg

[11394.252000] usb 1-1: new high speed USB device using ehci_hcd and address 6
[11394.384000] usb 1-1: configuration #1 chosen from 1 choice
[11479.824000] usb 1-1: USB disconnect, address 6
[11482.156000] usb 1-3: new high speed USB device using ehci_hcd and address 7


Sembla ser que detecta l'aparell i està connectat, però no s'obre cap pantalla.

---

### Post by farigola on 2007-11-26
He vist a un fòrum que aquest tipus de dispositiu ara per ara no és compatible. Per poder utilitzar aquest dispositiu només hi ha una opció que es Windows.

---

### Post by papapep on 2007-11-26
On ho posa això? No tot el que es publica és fiable...

---

### Post by farigola on 2007-11-26
He vist un web [http://www.anythingbutipod.com/archives/2007/10/samsung-ypt10-review.php](http://www.anythingbutipod.com/archives/2007/10/samsung-ypt10-review.php)
Que ara per ara no és possible fer transferències de fitxers fins l'aparició del driver MTP.

Transferring Media

The T10 is an MTP device meaning you will be limited to Windows XP SP2+ and Vista until someone writes some MTP drivers for Linux and Mac. Drag and drop does work very well with both Windows OSes, but if you want more functionality such as playlists, you will need to use a media player to manage those. 

Ara per ara no tinc altre que fer servir un Windows per actualitzar l'aparell. De totes maneres he vist un comentari recent que potser podria ser clau per no tenir que utilitzar Windows

I just got a Samsung T10 2GB. TO get it working with Amarok, I had to
download and compile libmtp 0.2.4. Now Amarok can see and upload mp3s to
the T10.

My problem is that the T10 supports OGG but Amarok wont upload OGG files. I
was using the Windows software for the T10 and upload an OGG file. To my
surprise it played without any problems. So, after upgrading libmtp I tried
to upload a few OGG files, but Amarok says the format isn't supported. When
I view the Special Features in Amarok, OGG isn't listed in the supported
media types.

Ara el problema està amb la compilació, de fet no fa ni 10 minuts que he obert un nou tiquet per fer referència a un problema de compilació.

---

