---
title: "No em munta les memòries USB"
date: 2011-03-14
forum: Catalan Team
---

### Post by Xicu Portas on 2011-03-14
Hola! Sóc nou en el món de Linux, tinc instal.lat l'Ubuntu 10.04 i tinc un problema.
Tinc tota la informació en un HD multimedia, l'iomega Screen Play Pro HD, si li faig un lsusb me'l veu però no tinc manera de poder-lo muntar i per tan no puc recuperar la informació.
També tinc un pendrive però aquest ni me'l veu.

xicu@xicu-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04fc:0015 Sunplus Technology Co., Ltd ViewMate Desktop Mouse CC2201
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 020: ID 059b:0473 Iomega Corp. [/COLOR]
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Algú em podria donar un cop de mà en aquest assumpte?
He provat varies coses que s'expliquen en aquest fòrum però no acosegueixo avançar.
Merci!

Xicu

---

### Post by quitus on 2011-03-14
Hola, intenta-ho amb un programet anomenat storage device manager, t'ajuda a configurar l'arxiu /etc/fstab que es el que s'encarrega de muntar els dispositius.

Et recomano desar una copia en algun lloc, pel que pugui passar.

salut

---

### Post by Xicu Portas on 2011-03-14
El programa storage device manager ja me l'havia instal.lat peró tot i aixó no me'l munta.

---

### Post by wgarcia on 2011-03-15
Desendollant el disc extern, i tornant-lo a endollar, des d'una terminal es pot donar la comanda 

dmesg

i mirar les últimes  línies a veure si es veu algun error del sistema respecte a la connexió usb al dispositiu.

---

### Post by Xicu Portas on 2011-03-15
despres de posar el terminal dmesg em surt una llista molt llarga i a les ultimes linies em surten els errors -71 i -110.

---

### Post by lpargemi on 2011-03-15
Jo quan tinc problemes amb unitats d'aquetes, els permisos d'accés etc. obro el programa "Utilitat de discs" -  ```
palimpsest
``` des del terminal, i miro què m'expliquen. Sovint em va millor desmuntant i tornant a muntar des d'aquest programa

Lluís

---

### Post by wgarcia on 2011-03-16
Però exactament què posen els errors que esmentes?

---

### Post by Xicu Portas on 2011-03-16
Aquest són els errors que em dona amb el dmesg

[  963.540033] usb 4-2: new full speed USB device using uhci_hcd and address 21
[  968.561468] usb 4-2: device descriptor read/8, error -110
[  973.681467] usb 4-2: device descriptor read/8, error -110
[  973.784052] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 1021.740027] usb 1-6: new high speed USB device using ehci_hcd and address 18
[ 1036.147875] usb 1-6: can't set config #1, error -71
[ 1036.147938] usb 1-6: USB disconnect, address 18
[ 1072.360037] usb 1-5: new high speed USB device using ehci_hcd and address 19
[ 1082.528728] scsi6 : usb-storage 1-5:1.0
[ 1115.152038] usb 1-5: reset high speed USB device using ehci_hcd and address 19
[ 1115.384032] usb 1-5: device descriptor read/64, error -71
[ 1115.744029] usb 1-5: device descriptor read/64, error -71
[ 1115.960028] usb 1-5: reset high speed USB device using ehci_hcd and address 19
[ 1116.224033] usb 1-5: device descriptor read/64, error -71
[ 1116.572043] usb 1-5: device descriptor read/64, error -71
[ 1116.788027] usb 1-5: reset high speed USB device using ehci_hcd and address 19
[ 1121.808130] usb 1-5: device descriptor read/8, error -110
[ 1126.928069] usb 1-5: device descriptor read/8, error -110
[ 1127.144037] usb 1-5: reset high speed USB device using ehci_hcd and address 19
[ 1132.164142] usb 1-5: device descriptor read/8, error -110
[ 1137.284084] usb 1-5: device descriptor read/8, error -110
[ 1137.388055] usb 1-5: USB disconnect, address 19
[ 1137.388071] scsi 6:0:0:0: Device offlined - not ready after error recovery
[ 1137.500531] usb 1-5: new high speed USB device using ehci_hcd and address 20
[ 1137.748025] usb 1-5: device descriptor read/64, error -71
[ 1138.144043] usb 1-5: device descriptor read/64, error -71
[ 1138.360025] usb 1-5: new high speed USB device using ehci_hcd and address 21
[ 1138.588024] usb 1-5: device descriptor read/64, error -71
[ 1138.920042] usb 1-5: device descriptor read/64, error -71
[ 1139.136059] usb 1-5: new high speed USB device using ehci_hcd and address 22
[ 1144.156174] usb 1-5: device descriptor read/8, error -110
[ 1149.276113] usb 1-5: device descriptor read/8, error -110
[ 1149.492050] usb 1-5: new high speed USB device using ehci_hcd and address 23
[ 1154.512191] usb 1-5: device descriptor read/8, error -110
[ 1159.632128] usb 1-5: device descriptor read/8, error -110
[ 1159.736066] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 1160.004066] usb 4-1: new full speed USB device using uhci_hcd and address 22
[ 1175.116593] usb 4-1: device descriptor read/64, error -110
[ 1190.332540] usb 4-1: device descriptor read/64, error -110
[ 1190.548029] usb 4-1: new full speed USB device using uhci_hcd and address 23
[ 1205.660036] usb 4-1: device descriptor read/64, error -110
[ 1220.876098] usb 4-1: device descriptor read/64, error -110
[ 1221.092031] usb 4-1: new full speed USB device using uhci_hcd and address 24
[ 1226.113261] usb 4-1: device descriptor read/8, error -110
[ 1231.233698] usb 4-1: device descriptor read/8, error -110
[ 1231.448529] usb 4-1: new full speed USB device using uhci_hcd and address 25
[ 1236.469150] usb 4-1: device descriptor read/8, error -110
[ 1241.589591] usb 4-1: device descriptor read/8, error -110
[ 1241.692062] hub 4-0:1.0: unable to enumerate USB device on port 1
xicu@xicu-System-Product-Name:~$

---

### Post by wgarcia on 2011-03-17
Està dient que el "HUB" USB provoca errors. Suposo que es tracta d'un HUB intern, oi? 

Poden ser dues coses:

1) un error del nucli en reconèixer el hub particular que fas servir. Per investigar-ho més es pot mirar el model amb:

sudo lshw | grep -i usb

Si quan comences l'ordinador veus altres nuclis des dels quals pots iniciar també pots provar si amb algun nucli més antic et surt l'error també.

2) Si és extern, mira si les connexions estan bé. A mi em donava aquest error amb un dispositiu USB per una connexió dolenta, la connexions USB són molt sensibles.

---

### Post by Xicu Portas on 2011-03-17
El hub de que parla ha de ser intern de la placa Asus p5kpl-cm.
Quan hi conecto el mòbil se'm connecta i desconnecta cada 2x3.
Però la webcam i el mouse em funcionen correctament.

El vespre miraré l'instrucció **sudo lshw | grep -i usb** a veure que em diu.

Però em temo que serà cosa de hardware.
Hauré de canviar la placa? 
O penjant un hub usb d'una de les entrades que em funcionen correctament serà suficient?

Moltes gràcies WGarcia!

---

### Post by Xicu Portas on 2011-03-17
Amb la comanda **sudo lshw | grep -i usb** em surt el següent:

xicu@xicu-System-Product-Name:~$ sudo lshw | grep -i usb
[sudo] password for xicu: 
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
xicu@xicu-System-Product-Name:~$

---

### Post by wgarcia on 2011-03-17
Per descartar que no sigui un problema de connexió del cable i la connexió USB intenta muntar el disc en algun altre ordinador. Els missatges que et surten a l'USB em semblen relacionats amb això.

---

### Post by Xicu Portas on 2011-03-17
He connectat el disc dur multimedia i el pendrive a un netbook amb windows i els dos funcinen correctament

---

### Post by kimet on 2011-03-17
Mira si pot ser això: [http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

---

### Post by Xicu Portas on 2011-03-17
Merci Kimet!
Ha anat de conya, no sé exactament que he fet però m'ha agafat el HD Multimedia i el pendrive.
Ara a veure si continua funcionant o ho he de fer cada vegada que els vulgui muntar.

---

### Post by Xicu Portas on 2011-03-22
Hola de nou!
El sistema que em va escriure en Kimet funciona però ho he d'entrar per terminal cada cop que vull muntar el disc dur extern o el pendrive.
Com ho puc fer perquè em funcioni sempre?
Gràcies.

---

### Post by Xicu Portas on 2011-03-26
Ja ho tinc solucionat, ja em munta les memòries cada cop que engego el PC.

Ha hagut d'editar el /etc/rc.local 

sudo gedit /etc/rc.local

i just abans del exit 0 i sense # afegir-hi:

cd /sys/bus/pci/drivers/ehci_hcd
ls
sudo sh -c 'echo -n "0000.00.xx.x"> unbid

les xx.x son diferents en cadascú, primer posar els comandament per separat en el terminal i et donara el que s'hi ha de posar, en el meu cas 1d.7

Merci a tots els que m'hi heu fet un cop de mà.

Salut.

---

