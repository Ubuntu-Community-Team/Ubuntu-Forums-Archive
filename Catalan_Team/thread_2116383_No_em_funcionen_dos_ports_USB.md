---
title: "No em funcionen dos ports USB"
date: 2013-02-15
forum: Catalan Team
---

### Post by Tiah on 2013-02-15
Bona nit
He recuperat fa pocs mesos un portàtil Compaq Presario C700 en el que hi vaig instal.lar l'Ubuntu 12.10. Dels tres ports USB que té només m'en funciona un. No sé si és un problema mecànic (la persona que el feia servir no recorda si li funcionaven els 3) o un problema de sistema ( no sé si en pot inhibir dos i deixar-ne un d'actiu). Com que no sé com comprovar-ho, seguint un fil d'aquest fòrum,  he executat ** lsusb** per veure si hi ha errors i m'ha respost:
[I]
Bus 001 Device 001: ID 1d6b: 0002 Linux Fundation 2.0 root hub
Bus 002 Device 001: ID 1d6b: 0001 Linux Fundation 1.1 root hub
Bus 003 Device 001:ID 1d6b: 0001 Linux Fundation 1.1 root hub
Bus 004 Device 001:ID 1d6b: 0001 Linux Fundation 1.1 root hub
Bus 001 Device 002:ID 174f:5212  Syntek USB 2.0 UVC PC Camera
Bus 003 Device 007:ID 1c4f:0003  SiGma Micro HID controller [/I]

Es pot deduir que tot està bé i que el problema és mecànic ja que no marca cap error?
Pot ser que la coincidència de nom dels bus 001 i 003 em bloquegi dues entrades USB?

A veure si algú em pot donar un cop de mà.

Moltes gràcies  per endavant

Tià

---

### Post by wgarcia on 2013-02-16
L' lsusb al meu parer es veu normal, al meu portàtil es veu molt semblant. 

Has mirat a la BIOS si tot es veu habilitat als ports USB? 

Una altra cosa que es pot provar és endollar algun dispositiu USB als ports que no funcionen, obrir una terminal, entrar l'ordre "dsmg" i mirar a les últimes línies si es veu algun missatge d'error, si el sistema està intentant detectar el dispositiu endollat.

---

### Post by Tiah on 2013-02-16
Gràcies i bon dia W,

Acabo de provar dmesg i després dmesg|grep -i usb (ho he trobat a [www.linfo.org]("http://www.linfo.org")). Les dues orfdres em donen una informació semblant  

[223.564145] usb 1-3: new high-speed USB device number 3 using ehci_hcd
[  223.698897] hub 1-3:1.0: USB hub found
[  223.699342] hub 1-3:1.0: 4 ports detected
[  223.988155] usb 1-3.2: new low-speed USB device number 4 using ehci_hcd
[  224.291641] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.2/1-3.2:1.0/input/input9
[  224.291881] generic-usb 0003:15D9:0A4F.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.7-3.2/input0
[  224.292996] usbcore: registered new interface driver usbhid
[  224.293001] usbhid: USB HID core driver
[COLOR=Red][B][  668.746154] usb 1-3: USB disconnect, device number 3
[  668.746158] usb 1-3.2: USB disconnect, device number 4[/B][/COLOR]
[  672.936119] usb 3-1: new low-speed USB device number 2 using uhci_hcd

Entenc que les dues linies que remarco en vermell diun que tinc dos ports desconnectats. Ara no sé si el problema bé d'alguna cosa que explica més amunt o es tracta senzillament de connectar-los ... però com?

Gràcies per la vostra ajuda.

PD: Això d'brir el terminal tot i ser "excitant" em fa un xic de respecte vista la meva innexpreriència!!!!

--------------------------------------------------------

reedito el missatge:
m'oblidava de comentar que tal com deia en wgarcia  he endollat un pendrive a un dels ports i, evidentment, (a diferència del rratolí) no el detecta.

---

