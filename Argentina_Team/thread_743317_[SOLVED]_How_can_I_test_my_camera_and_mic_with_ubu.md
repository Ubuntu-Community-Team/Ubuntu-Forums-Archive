---
title: "[SOLVED] How can I test my camera and mic with ubuntu?"
date: 2008-04-02
forum: Argentina Team
---

### Post by santisantermer on 2008-04-02
Hi, I'm new in ubuntu and I've a lot of problems with elements of my notebook that doesn't work. However I couldn't test my build-in camera and microphone. Does anybody know can I do that?
Thanks a lot!

---

### Post by blazercist on 2008-04-02
sudo apt-get install camorama

---

### Post by sajnox on 2008-04-02
Folks,

This is the Argentinean Forum, everybody is welcome to post here, but...obviusly please do it in spanish

Thanks

---

### Post by Hei Ku on 2008-04-02
Che, nos estan invadiendo los piratas!!! Justo el 2 de abril!!! 

:lolflag:

---

### Post by faktorqm on 2008-04-02
si parece que lo estan haciendo a proposito :@, manga de gatos! nos estan cascoteando el rancho! (a ver si pueden traducir eso con el traductor de google JAJAJAJAJAJA)

---

### Post by User21 on 2008-04-03
> **faktorqm said:**
> si parece que lo estan haciendo a proposito :@, manga de gatos! nos estan cascoteando el rancho! (a ver si pueden traducir eso con el traductor de google JAJAJAJAJAJA)
JAJAJA, te pasás, viejo! :lolflag:

---

### Post by vk-cdg on 2008-04-03
> **faktorqm said:**
> si parece que lo estan haciendo a proposito :@, manga de gatos! nos estan cascoteando el rancho! (a ver si pueden traducir eso con el traductor de google JAJAJAJAJAJA)

Jajajajaja, entré para leer tu post solamente. Sabía que no te ibas a poder contener de postear algo.

Te faltó poner recatate locooo!

---

### Post by felipelerena on 2008-04-03
esos pisperietos... (sigo la onda del translator)

---

### Post by santisantermer on 2008-04-04
Hola, muchas gracias por la sugerencia, la voy a probar. No soy ningún pirata inglés en busca de una colonia. 
Lo que pasó es que me metí al foro de Argentina y me direccionó a otro en el que todos los mensajes estaban escritos en inglés y tuve que crear nuevamente el usuario para poder escribir ahí. Obviamente, supuse que estaba en el foro de un país de habla inglesa y por eso hice la consulta en ese idioma. Pero me alegra saber que realmente hay un foro en español.
Un abrazo,
Santiago

---

### Post by santisantermer on 2008-04-08
Hola, probé con camorama y me aparece un mensaje de error. Dice que no pudo conectarse con el dispositivo de video (/dev/video0) y que por favor verifique la conexión.
Creo que lo que me salió al poner el comando Ispci, le va a ser de utilidad a quien quiera ayudarme.
Realmente valoraré toda la ayuda que puedan darme.
Muchas gracias.
Santiago.



santiago@santiago-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
santiago@santiago-laptop:~$

---

### Post by sdennie on 2008-04-09
Camorama no anda con la laptop mia tampoco porque el driver solo funciona con v4l2 (video for linux 2).  Fijate en gstreamer-properties (Alt-F2 gstreamer-properties) a ver si podes probarlo desde alla con v4l2.

---

### Post by santisantermer on 2008-04-09
Buenisimo!!!! Hice lo que me dijiste, puse probar y anduvo.
Muchas gracias a todos. Problema solucionado.
Saludos,
Santiago.

---

### Post by User21 on 2008-04-10
Ponle** Mark as SOLVED** al hilo, desde el menu Thread Tools !

---

### Post by santisantermer on 2008-04-10
Ya lo hice hace unos dias. A mi me aparaece como (solved). Además, ya no me aparece esa opción en thread tools.
Tengo que hacerlo otra vez? Como seria?.
Saludos,
Santiago.

---

