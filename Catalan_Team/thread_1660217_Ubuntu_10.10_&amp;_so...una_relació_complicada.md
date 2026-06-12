---
title: "Ubuntu 10.10 &amp; so...una relació complicada"
date: 2011-01-05
forum: Catalan Team
---

### Post by txotxi on 2011-01-05
Hola, fa uns dies vai actualitzar l'ubuntu al 10.10 per un "problemilla" que tenia amb l'anterior versió i el wifi.
amb l'actualització les conexions amb la xarxa es van arreglar, però el que m'ha succeït és que m'he quedat sense so.
he obert la terminal i posant lspci, hem surt això:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

la veritat és que no controlo gaire però us ho poso per veure si algú hem pot donar un cop de mà.

Gràcies

---

### Post by wgarcia on 2011-01-05
Al que has enganxat no es veu cap dispositiu d'àudio. Què surt si entres a una terminal:

aplay -l

?

---

### Post by txotxi on 2011-01-06
Al posar el que m'has dit hem urt això:

aplay: device_list:235: no soundcards found...

Amb la versió anterior no tenia cap problema, però amb aquesta no escolto res i la veritat és que no se que succeeix ja que jo no controlo gaire.

---

### Post by wgarcia on 2011-01-06
És estrany, sembla que tens una targeta d'àudio Intel de la família ICH8 integrada a la placa mare, però el sistema no la detecta. Una primera prova molt simple que es pot fer és veure si no és simplement un problema d'electricitat estàtica que anul·li la targeta momentàniament. Pots provar de treure la bateria, i amb l'ordinador desendollat de la corrent elèctrica prémer el botó d'arrencada uns 30 segons, i després iniciar l'ordinador i tornar a fer "aplay -l" a veure  si ara veu la targeta de so?

---

### Post by txotxi on 2011-01-06
hem sembla que no la detecta:
aplay: device_list:235: no soundcards found...

---

### Post by wgarcia on 2011-01-06
Bé, primer s'havia de provar el més simple. Ara es pot provar una altra solució que sembla que ha funcionat per a d'altres que tenen la teva mateixa targeta de so. Obre una terminal (Accessoris -> Terminal) i entra 

sudo gedit /etc/modprobe.d/alsa-base.conf

i agrega la línia següent al final:

options snd-hda-intel probe_mask=1


Reinicia a veure si ara veu la targeta.

---

### Post by txotxi on 2011-01-07
Doncs no la detecta:
aplay: device_list:235: no soundcards found...

no ho se, jo es que no se que fer!

---

### Post by kimet on 2011-01-07
-El primer que hauries de saber es la targeta que tens i el mòdul que li correspón.
Prova amb un liveCD de fer:
```
lspci|grep Audio
```
Si trobes resposta sabràs la targeta que tens.

Verifica si s'han carregat els mòduls
```
lsmod|grep snd
```
Et retornarà els mòduls de so que tens instal.lats.
Carregues els mòduls que et falten:
```
sudo modprobe snd_hda_intel  

```
Suposant que la targeta sigui una intel hda.(es probable)

Torna a verificar: 
-Si detecta la targeta.
-Si el teu usuari pertany al grup audio.

---

### Post by txotxi on 2011-01-07
Segueix sense reconèixer la targeta de so.

---

### Post by wgarcia on 2011-01-07
Tens un CD d'instal·lació d'Ubuntu per provar si entrant en mode Live (sense instal·lar) tens so?

---

### Post by txotxi on 2011-01-07
amb el live cd no tinc so tampoc.
potser es cosa de l'ordenata!!

---

### Post by wgarcia on 2011-01-08
Després d'una actualització jo també vaig pensar que m'havia quedat sense so, i va resultar que els altaveus tenien un mal contacte, no ho descartis. Ara bé, si proves un Live CD d'Ubuntu 10.04 i tens so, i amb la 10.10 no ho tens, llavors sí que es pot atribuir a l'actualització.

---

### Post by txotxi on 2011-01-10
Doncs he anat provant varies versions de l'Ubuntu i amb cap tinc so, potser si que és un problema tècnic.
provarem de portar-lo al mecànic a veure que diu.

Gracies per l'ajuda!

---

