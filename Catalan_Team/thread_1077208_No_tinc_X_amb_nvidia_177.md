---
title: "No tinc X amb nvidia 177"
date: 2009-02-22
forum: Catalan Team
---

### Post by dmartinez116 on 2009-02-22
Hola de nou, després de fer funcionar perfectament el meu compaq cq60-125es amb l'ajuda de papapep, ací torne de nou amb el desktop.

El meu pc te dues targetes gràfiques pciexpress, una 7300 i una 8500 ambdos de nvidia.

Ahir vaig instal·lar el 8.10 i com que tinc dos monitors enganxats a la 8500 durant la instal·lació als dos es veia el mateix. Vaig buscar actualitzacions, les vaig descarregar i instal·lar (2 hores aprox) vaig marcar uns quans paquets que solc fer servir (VLC, amule, compiz icon, etc...) i també vaig habilitar el mòdul de nvidia 177.

Tot perfecte fins que vaig reiniciar, no m'apareixien les X... cachis!

Vaig provar el recovery mode del grub, vaig tractar de recuperar les X, i ara se'm queda en Checking battery state. La consola funciona, però les X no.

Ací vos mostre l'eixida del lspci (per a que no me'l demaneu):

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

```

Gràcies a tots.

---

### Post by dmartinez116 on 2009-02-23
Hola, ja se que vos he soltat un rotllo prou gran, però ningú sap que puc fer?

Al menys per a recuperar les X... es pot deshabilitar el modul de nvidia, o arrancar el sistema en mode segur de gràfics (com en XP)?

Vinga, segur que a algú se li ocorre algo.

Gràcies.

---

### Post by tanreb20 on 2009-02-23
Una opció que podries probar es esborrar l'arxiu 

```
xorg.conf
``` i al arrencar t'en generara un d'automatic.

---

### Post by dmartinez116 on 2009-02-23
Gràcies tanreb20, ho prove i et dic alguna cosa.

---

### Post by dmartinez116 on 2009-02-23
Be, després de fer la prova continue igual.

Es queda en *Checking battery state*

La consola (Ctrl+Alt+F1) funciona, però ni rastre de les finestres.

---

### Post by corretge on 2009-02-24
Mira que no sigui que el driver nvidia 177 estigui compilat amb un kernel diferent del que estàs executant.

Jo per uns problemes amb twin view faig servir el driver d'nvidia 177.70 baixat de la casa nvidia doncs estic a 8.04 i no funcionaven els del repositori, i cada cop que actualitzo el kernel he de mirar de compilar-ho de nou doncs si no no arrenquen les X.

---

### Post by dmartinez116 on 2009-02-25
Be, jo no tinc molt de nivell amb linux, així que et responc al que hem preguntes des de la ingnorància, si no és això el que preguntes, et demane disculpes i també que m'ho tornes a preguntar, jeje.

Jo vaig instal·lar el 177 de nvidia del repositori. Ara mateix no tinc davant el pc amb problemes, però el seu kernel és l'ultim, el vaig actualitzar abans d'instal·lar els nvidia 177. També he provat a reiniciar en l'anterior kernel que apareix al grub amb semblants resultats.

No se que és twin view, i tampoc com compilar el driver.

Continue sense X, més idees?

Gràcies.

---

### Post by dmartinez116 on 2009-02-27
A ubuntu no tenim alguna manera de arrancar amb el mode vga o vesa standar?

El live-cd funcionava perfectament... com puc recuperar les x's sense haver de reinstal·lar de nou?

Gràcies.

---

### Post by papapep on 2009-02-27
> A ubuntu no tenim alguna manera de arrancar amb el mode vga o vesa standar?

Evidentment. Quan comença l'arrencada, diu alguna cosa semblan a "Prem Esc per aturar". Si ho fas, veuràs el menú on, entre altres, hi haurà l'opció "Mode gràfic segur".

---

### Post by dmartinez116 on 2009-02-27
Gràcies papapep, et referèixes al grub? o després del grub mentre ix la paraula ubuntu i una barra de progres de color carabassa?

---

### Post by papapep on 2009-02-27
Ostres, no ho recordo, però provant ho sabràs... :)

---

### Post by dmartinez116 on 2009-02-28
Be, pues provant... no ho he vist...

Al grub hi ha recovery mode... que no és el mateix que mode gràfic segur.

I si presione ESC mentre carrega UBUNTU... no fa res...

Més ajuda, per favor.

---

### Post by dmartinez116 on 2009-03-01
Hola de nou, ací torne amb més info.

Hui que tenia temps, m'he decidit a començar de nou.

He esborrat del disc dur totes les particions que tenien a vore amb l'ubuntu.

He recuperat l'espai, he reiniciat i he inserit el live cd del 8.10.
He fet una instal·lació neta. He reiniciat.
He instal·lat el suport d'idioma complet. He reiniciat
He habilitat el 177 de nvidia i al reiniciar... voilá.... es repeteix l'error, però esta vegada vos puc transcriure el que em deia abans de fer server el recovery mode:

```

Boot from (hd1,4) ext 3 c7c013a3-81c2-49e7-89e9-e1e099e3ecc5
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/byuuid/f652ba7a-2f2f-4586-b7f1-1955c9f29cbb) = dev(8,22)
kinit: trying to resume from /dev/disk/byuuid/f652ba7a-2f2f-4586-b7f1-1955c9f29cbb
kinit: No resume image, doing normal boot...


Ubuntu 8.10 dubuntu tty1
dubuntu login:

```

I així es queda.

Ho he transcrit tot a mà des del portatil (poden haver-hi errors)

He tractat de fer login i llançar startx però hem diu "no screens found, giving up."

---

### Post by dmartinez116 on 2009-03-01
Tot resolt, gràcies a tot el mon.

La solució l'he trobada ací:
[http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start](http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start)

He seguit el post #2 i tot resolt, ja tinc les dos nvidia funcionant amb twinview i el compiz... ES-PEC-TA-CU-LAR.

Cada vegada m'agrada més l'ubuntu (i això que em fa patir...) sere masoca?

---

### Post by CarlesOriol on 2009-03-02
COMPTE, WARNING, ALERTA !!!!!!!!!!!!!!!!!!!!!!!!

Els controladors 180 d'nvidia peten.

[http://www.phoronix.com/scan.php?page=news_item&px=NzEwMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzEwMQ)

---

### Post by dmartinez116 on 2009-03-02
Gràcies per l'avis.

Jo no he tingut eixe problema que descriu el teu link.

Si tinc problemes al iniciar, quan deuria apareixer l'escriptori es queda negre i al fer ctrl+alt+F1... és reinicia.

Si arranque en recovery mode puc fer servir la consola per a reparar la instal·lació del driver de Nvidia i tot resolt.

Em fixaré be, perque jo pensava que el problema era que estic barallant-me amb una A16D de avermedia i pensava que era este maquinari el que donava problemes i no el driver de nvidia... però ara que ho dius... pot estar relacionat.

---

