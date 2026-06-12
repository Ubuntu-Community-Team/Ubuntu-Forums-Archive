---
title: "Ubuntu no detecta el disc extern"
date: 2009-04-21
forum: Catalan Team
---

### Post by Eloio on 2009-04-21
Bona tarda,
Ja sé que molts de vosaltres pensareu que no he fet una cerca a google abans de penjar aquest post, però creieu-me he estat navegant per totes les pàgines possibles i no aconsegueixo que el el disc extern s'executi en obrir-lo amb l'ubuntu. Amb el vista s'obre, és a dir que el disc funciona. D'altres pen-drives s'obren amb l'ubuntu cosa que significa que no es una cosa de ports...
He provat també d'escriure solucions que trobava per d'altres persones que tenien aquest problema en el terminal i res...

Algú em cableja?

Gràcies!

---

### Post by Miquel Ubuntero on 2009-04-22
Bones.
Per tindre una mica més d'informació.
Podries des de Terminal fer lsusb a veure si està el disc detectat.
Pot ser si tens el un editor de particions insta&#320;lat podries fe-hi un cop d'ull.
Ja diràs.
Salut!

---

### Post by guillemsola on 2009-04-22
Crec que també podria ser interessant un "dmesg | tail" just després de connectar el disc usb.

salutacions

---

### Post by fballem on 2009-04-22
I'm sorry that I don't speak Spanish, but is this bug related to the question that you are asking?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034)

Hope this helps,

---

### Post by oriolsbd on 2009-04-23
Hola, a més del "dmesg", i el "lsusb" (executa'ls, segur que et donaran moltes pistes de què pot estar passant) has provat d'engegar l'ordinador amb el disc ja connectat i engegat?

Salut!

---

### Post by Miquel Ubuntero on 2009-04-23
> **fballem said:**
> I'm sorry that I don't speak Spanish, but is this bug related to the question that you are asking?

We also don't use spanish language in this foro. We speak/writte in Catalan language, as we are a Catalan Loco Team.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034)

Hope this helps,
Thanks for your help.
Greatings from Catalonia. ([http://en.wikipedia.org/wiki/Catalonia](http://en.wikipedia.org/wiki/Catalonia))

---

### Post by Eloio on 2009-04-25
Gràcies a tot*s els que heu contestat. Aquí us envio les dades que demanàveu!


eloi@eloi:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


eloi@eloi:~$ dmesg | tail
[  343.435226] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input7
[  343.458406] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[  343.487339] Fixing up Logitech keyboard report descriptor
[  343.490071] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input8
[  343.526422] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[  343.526460] usbcore: registered new interface driver usbhid
[  343.526470] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  118.612088] usb 3-2: new high speed USB device using ehci_hcd and address 3
[  463.004680] usb 3-2: new high speed USB device using ehci_hcd and address 4
[  463.492512] usb 3-2: new high speed USB device using ehci_hcd and address 6



Moltes gràcies altre cop!

Eloi

---

### Post by Eloio on 2009-04-28
> **Miquel Ubuntero said:**
> Bones.
Per tindre una mica més d'informació.
Podries des de Terminal fer lsusb a veure si està el disc detectat.
Pot ser si tens el un editor de particions insta&#320;lat podries fe-hi un cop d'ull.
Ja diràs.
Salut!

eloi@eloi:~$ lsusb
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000

---

### Post by Eloio on 2009-04-28
> **angrychai said:**
> Crec que també podria ser interessant un "dmesg | tail" just després de connectar el disc usb.

salutacions

Aquí tens la info que demanaves... :

eloi@eloi:~$ dmesg | tail
[ 343.435226] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input7
[ 343.458406] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[ 343.487339] Fixing up Logitech keyboard report descriptor
[ 343.490071] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input8
[ 343.526422] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[ 343.526460] usbcore: registered new interface driver usbhid
[ 343.526470] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 118.612088] usb 3-2: new high speed USB device using ehci_hcd and address 3
[ 463.004680] usb 3-2: new high speed USB device using ehci_hcd and address 4
[ 463.492512] usb 3-2: new high speed USB device using ehci_hcd and address 6

Gràcies!

---

