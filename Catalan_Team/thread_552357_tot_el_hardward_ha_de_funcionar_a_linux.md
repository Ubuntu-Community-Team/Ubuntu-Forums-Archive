---
title: "tot el hardward ha de funcionar a linux"
date: 2007-09-16
forum: Catalan Team
---

### Post by muleta on 2007-09-16
He hagut de renunciar a la multifunció perque és incompatible amb Linux i ho intento compensar instal·lant un antic scanner ScanMagic 1200 CP, de port paral·lel amb el seu adaptador a USB i un driver A4 EPP Scanner per a W 95, 98, NT 4.0.

He contactat amb un grup de linuxers que postula que s'ha de poder instal·lar tot el hardward a Linux però, de moment, a part de reclamar als fabricants, no troben una solució per al meu scanner, tot i que l'estan investigant.

Tinc instal·lat el Sane però no veu l'ScanMagic.

Sé que la manera fàcil de resoldre-ho és llençar tots els perifèrics i comprar-ne de nous per a Linux, però no m'han agradat mai les sortides fàcils.

Algun suggeriment?. No em val el de tornar a Windows, encara no ](*,)](*,)](*,)[-X

---

### Post by RainCT on 2007-09-16
Podríes provar a veure si te'l veu el Kooka. A mi el Sane no me n'ha vist mai cap (o no he aconseguit entendre com es fa servir :P), però amb el Kooka els dos que tinc (un d'ells multifunció) em van perfectament.

---

### Post by CarlesOriol on 2007-09-16
Rain. El motor del kooka és el sane

---

### Post by muleta on 2007-09-16
Al·leshores, com és que li funciona?.

---

### Post by CarlesOriol on 2007-09-16
Per que el sane li funciona. :-)

Hi ha altres forntends per gnome el **xsane** que està igual de bé i en linia de comandes el **scanimage** (aquest és molt divertit). Aa més d'altres programes que usen el sane com el **openoffice** i el **sane2pdf**.

Podem dir que el sane és standard de facto com ho era el twain en hasefrog.

---

### Post by muleta on 2007-09-16
Bé, potser no estem parlant del mateix.

Jo voldria instal·lar l'scanner. El control·lador que porta és per a port paral·lel i, com que només tinc ports USB en el portàtil, l'he connectat amb un adaptador que sembla no realitzar cap més funció que la de cable allargador de la connexió.

Com que no tinc driver, m'aconsellen que recorri al Sane perque me'n trobi un de genèric però el Sane em diu que no hi ha cap scanner endollat.

Hi ha manera de saber si no el veu perque no el coneix o perque l'adaptador ho espatlla tot?.

No em funciona el Xsane ni el Kooka ni trobo l'scanimage en els repositoris. Però, segur que m'ajudarien a trobar un control·lador genèric?.

---

### Post by patrickfromspain on 2007-09-16
Els adaptadors usb->por para&#320;el o usb->por serie, no son adaptadors: son ports externs, per aixo necessiten un driver i tot aixo...

Inicia linux sense cap dispositiu enxufat: ni scanner, ni impresora ni adaptador. ves a terminal i fes: cd Desktop && lsusb > lsusb.log1 && dmesg > dmesg.log1 i tanca terminal

Llavors enxufa l'adaptador (sense escaner ni res), obre un terminal i: cd Desktop && lsusb > lsusb.log2 && dmesg > dmesg.log2 i torna a tancar el terminal 

Fet aixo, tindras 4 arxius nous a l'escriptori. Selecciona'ls, crea un arxiu .tar.gz i penja'l aqui. Igual veiem algo.

Salut!

---

### Post by muleta on 2007-09-16
Aquí el teniu. Què veieu?.

---

### Post by patrickfromspain on 2007-09-17
en principi, hem sembla que si et detecta "l'adaptador":

[  209.484000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  209.684000] usb 1-1: configuration #1 chosen from 1 choice
[  209.916000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
[  209.920000] usbcore: registered new interface driver usblp
[  209.920000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

Pero no se si ho fa de manera correcta, ja que hi diu USB printer.. al fer el 2on dmesg, segur que nomes vaig enxufar l'adaptador, oi?

---

### Post by muleta on 2007-09-17
Sí, però, quan vaig connectar l'adaptador (desconnectat de l'scanner), em va sortir el quadre de diàleg que em surt cada vegada que connecto l'impressora demanat-me si la vull tornar a instal·lar. Es deu fer algun embolic.

---

