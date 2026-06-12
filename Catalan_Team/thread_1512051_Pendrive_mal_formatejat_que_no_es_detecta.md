---
title: "Pendrive mal formatejat que no es detecta"
date: 2010-06-17
forum: Catalan Team
---

### Post by joaquimrubio on 2010-06-17
He volgut crear un disc d'arrencada i per començar he volgut formatar un pendrive de 1 GB. Però al formatar un pendrive de 1GB, (prémer ratolí esquerre i demanar formatar), m'ha donat un missatge d'error, deia en anglès quelcom similar a que "la memòria era incapaç de formatar-se al FAT que li havia demanat per falta de capacitat de clusters" i a continuació l'ordinador ha deixat de detectar el pendrive, la llumeta del pendrive s'encén però el KK 9.10 no el detecta.

Amb la consola, amb el comandament mount, tampoc apareix.

Que és pot fer per tal de que torni a aparèixer?

---

### Post by Diegstroyer on 2010-06-19
Que et diu si poses **lsusb** en una terminal?

---

### Post by joaquimrubio on 2010-06-22
Surt això amb la memòria flash connectada:

joaquim@joaquim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 002: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joaquim@joaquim-desktop:~$ 

I surt això un cop l'he tret: 

joaquim@joaquim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 002: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joaquim@joaquim-desktop:~$ 

Em penso que és lo mateix.

---

### Post by joaquimrubio on 2010-06-22
Ara he formatejat una altra memòria de 1 GB, de la marca Data Traveller, no hi ha hagut cap sorpresa, l'he formatejat a arxius ext 3 i sí que apareix:

joaquim@joaquim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 002: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joaquim@joaquim-desktop:~$

---

### Post by joaquimrubio on 2010-06-22
Perdò, sí que el detecta, tal com es veu en aquesta còpia de la consola (he desconnectat alguns altres usb per a simplificar):

Amb el pendrive:

joaquim@joaquim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joaquim@joaquim-desktop:~$ 

Sense el pendrive:

joaquim@joaquim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I veig que la consola detecta tant aquest que esta formatat a FAT com un altre que he formatat a ext 3 i un tercer que he formatat a FAT altre cop, ho sigui, els detecta tots via consola, però a l'escriptori només apareix un dels que he formatat a FAT, l'altre formatat a FAT i l'altre formatat a ext 3 no m'apareixen.

---

### Post by Diegstroyer on 2010-06-22
mmm... força estrany, normalment, encara que no les reconegui, haurien d'aparèixer al lsusb, normalment, si no ho fan, es que no funcionen.

Tots els que apareixen a lsusb funcionen bé, prova d'arrencar amb LiveCD d'ubuntu a veure si tels munta allà.

Pots provar el Gparted també a veure si els pots tornar a reformatar.

Et funcionen en altres ordinadors?

---

### Post by joaquimrubio on 2010-06-22
Diegstroyer, ens hem creuat les contestacions. La consola detecta les memòries, però 2 de les tres memòries no apareixen a la consola.

---

### Post by joaquimrubio on 2010-06-22
Perdò, vull dir que sí apareixen les 3 memòries a la consola però només una a l'escriptori Gnome de l'ordinador. Ara només tinc un ordinador aquí, ja ho provaré en el portàtil que és a la feina.

---

### Post by joaquimrubio on 2010-06-22
Diegstroyer, moltes gràcies, he fet el que deies i amb la Utilitat de discs (Sistema, Administració, Utilitat de Discs) els he pogut detectar i tornar a formatar. Però el que he formatat a ext 4 no apareix a l'escriptori Gnome, els altres, formatats a FAT 32, sí que hi apareixen. A la consola i a la utilitat de discs hi apareixen tots.

És normal, això?

---

### Post by joaquimrubio on 2010-06-22
Aquest és el missatge que apareix al pendrive de 1 GB quan el vull formatar des de la utilitat de discs:

Error creating file system: helper exited with exit code 1: helper failed with:
WARNING: Not enough clusters for a 32 bit FAT!
mkfs.vfat: Attempting to create a too large file system

La consola el detecta. La utilitat de discs, també. No apareix a l'escriptori Gnome.

Amb un altre pendrive de 1 GB i amb un altre pendrive de 250 MB, la consola els detecta, apareixen a la utilitat de discs i apareixen a l'escriptori Gnome.

Això vol dir que el primer pendrive està espatllat?

---

### Post by joaquimrubio on 2010-06-22
Seguint trastejant per curiositat, ja que dono la memòria per perduda, he baixat el programa Gparted i he anat a la pestanya visualitza i hem deia que aquest pendrive tenia 243 MB enlloc de 1GD que és el que té, el llegia malament. He volgut crear una taula de particions (Dispositiu, Crear taula de particions,) he escollit el msdos preconfigurat i m'ha passat una cosa ben curiosa, que per això la detallo a aquest forum: El programa Gparted es tanca sol. Si desconnecto aquesta memòria i no en connecto cap o en connecto una altra, el programa s'engega amb normalitat i funciona amb normalitat. Si deixo connectada aquesta memòria, el programa Gparted no arriba a engegar. Si connecto aquesta memòria un cop el programa Gparted ja està engegat, el programa es tanca sol.
Ben curiós, oi?
No sé si Sergistroyer o algú altre hi voldrà afegir quelcom.

Com sempre, gràcies a tots els que ajudeu.

---

### Post by Diegstroyer on 2010-06-23
Si no el pots obrir és molt provable que estigui espatllat.

Que et diu;** sudo fdisk -l**

Prova d'instalar **pmount **i **usbmount** des de synaptic, reinicia l'ordinador i mira a veure si el monta. Prva també el Gparted a veure.

Aquest error fa referència als clusters, pot ser que tingui algun sector malmès.

Si no funciona prova el LiveCD i ens comentes.

Salutacions.

---

### Post by joaquimrubio on 2010-06-23
He fet el sudo fdisk -l i hem surt aquesta parrafada:

 Disc /dev/sdd: 3970 MB, 3970392576 octets
123 heads, 62 sectors/track, 1016 cylinders
Units = cilindres of 7626 * 512 = 3904512 bytes
Disk identifier: 0x6f20736b

Això no sembla cap taula de particions
Probablement heu seleccionat un dispositiu incorrecte.
Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdd1   ?      102038      251724   570754815+  72  Desconegut
La partició 1 té diferents començaments físics/lògics (no Linux?):
     físic=(357, 116, 40) lògic=(102037, 28, 11)
La partició 1 té diferents finals físics/lògics:
     físic=(357, 32, 45) lògic=(251723, 95, 51)
La partició 1 no acaba en un límit de cilindre.
/dev/sdd2   ?       22121      275993   968014120   65  Novell Netware 386
La partició 2 té diferents començaments físics/lògics (no Linux?):
     físic=(288, 115, 43) lògic=(22120, 38, 47)
La partició 2 té diferents finals físics/lògics:
     físic=(367, 114, 50) lògic=(275992, 44, 42)
La partició 2 no acaba en un límit de cilindre.
/dev/sdd3   ?      245199      499071   968014096   79  Desconegut
La partició 3 té diferents començaments físics/lògics (no Linux?):
     físic=(366, 32, 33) lògic=(245198, 24, 30)
La partició 3 té diferents finals físics/lògics:
     físic=(357, 32, 43) lògic=(499070, 29, 39)
La partició 3 no acaba en un límit de cilindre.
/dev/sdd4   ?      378401      378408       27749+   d  Desconegut
La partició 4 té diferents començaments físics/lògics (no Linux?):
     físic=(372, 97, 50) lògic=(378400, 44, 25)
La partició 4 té diferents finals físics/lògics:
     físic=(0, 10, 0) lògic=(378407, 78, 33)
La partició 4 no acaba en un límit de cilindre.

Les entrades a la taula de particions no estan en l'ordre del disc
Nota: la mida del sector és 2048 (no 512)


Segueix passant lo mateix que ahir: 
L'escriptori Gnome no el detcta, la consola sí, la utilitat de discs sí i el Gparted el detecta a l'engegar però a continuació s'apaga el Gparted. Si aquest pendrive no esta connectat, el Gparted funciona amb normalitat.

---

### Post by Diegstroyer on 2010-06-28
Has fet les altres coses que et comento?

---

### Post by joaquimrubio on 2010-06-30
Vaig baixar els 2 programes pmount i usb mount amb el sinaptic tal com em deies que fes. Vaig reiniciar i amb el pendrive, igual que abans. Els 2 programes estan instal·lats ja que el sinaptic ho marca així però no apareixen a cap llista, a diferència del Gparted que sí apareix. 
No he fet lo del Live CD ja que no entenc exactament que he de fer. Tinc el CD del Karmic i ja tinc el pendrive del 10.04 Lucid Linx.

Gràcies Sergistroyer.

---

### Post by Diegstroyer on 2010-07-01
Els paquets que et cometo que t'instal·lis son eines que utilitza el kernel per reconèixer i muntar usb.

Amb el CD de Lucid, o Karmic, arrenca des de el CD, i sense instal·lar el SO posa el USB a veure si el munta a l'escriptori del LiveCD.

Salutacions.

---

### Post by ofde on 2010-07-26
Jo vaig tenir un problema semblant amb una memòria d'un Gb i amb  el disk utility el vaig resoldre, crec recordar que havia de desmuntar la unitat usb abans de fer el formateig.
Un altra possibilitat es que ho provis en un sistema windows, viam si allà el pots fer funcionar i formatejar.

---

### Post by akyra on 2010-07-27
Jo sempre he formatejat qualsevol dispositiu amb el Gparted, i sempre s'ha de desmuntar el dispositiu abans de fer res.
Una vegada desmuntat, des del mateix Gparted, ja es pot formatejar.

Salutacions

---

### Post by joaquimrubio on 2010-07-27
He provat el mode live amb el CD Ubuntu 9.10 i el Gnome tampoc el detecta, sí el lsusb.
El Gparted sí el detecta i si el vull formatar es tanca i apareix un missatge similar a "Crashes Report: Sorry, Gparted closed unexpectadly..."

He provat de accedir-hi i de formatar amb W-7 i em respon que Windows no pot formatar la unitat. W-7 el detecta però no hi pot accedir.

Si el desmunto amb la utilitat de discs, no el detecto i per tant, no el puc formatar.

Gràcies a tots, però dono el Pendrive per perdut, deu tenir alguna cosa de hardware espatllada, penso que no val la pena perdre-hi més temps.

Vull agraïr i remarcar lo útil que m'ha sigut aquest fil, coneguent una sèrie de manaments per a la consola i obrint la ment a altres opcions per aconseguir un fi per un altre camí quan el primer intent no funciona.

Gràcies a tots.

Joaquim

---

