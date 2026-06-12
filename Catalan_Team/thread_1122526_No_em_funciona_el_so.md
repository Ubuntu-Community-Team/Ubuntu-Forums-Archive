---
title: "No em funciona el so"
date: 2009-04-11
forum: Catalan Team
---

### Post by lo gambusí on 2009-04-11
Hola!

Bona fi de vacances.


Des de fa un parell de setmanes no em funciona el so. No recordo haver instal·lat ni desinstal·lat res que pugue afectar, ni haver fet cap canvi de configuració important.

Copio el que em surt al dir-li lspci a la terminal. No sé si pot ser útil.

> logambusi@logambusi-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


Gràcies,a vore si em podeu ajudar!!):P

---

### Post by Mr-Biscuit on 2009-04-11
Nao sei catalan, somente portuguesa e castelhano.
Ok.
tentou alsaconfig? 
As vezes, environmentes como assim GNOME precisa de usar esound ou um versao do esound. tentou esound?

Usando alsaconfig uma outra vez podia correctar sua problema.

.........
talvez usted necesita de usar alsaconfig en el CLI.

---

### Post by lo gambusí on 2009-04-11
Ho sento, però no entenc el portuguès. Gràcies.
[I]
I'm sorry but I don't understand portuguese.Thanks.

Je suis desolé mais je comprends pas le portugais. Merci.[/I]

---

### Post by torracastanyes on 2009-04-11
Traduïnt pel broc gros, M. Biscuit ve a dir:

"No sé català, només portuguès i castellà
Bé
Has provat l'Alsaconfig?
De vegades, els entorns com ara gnome necessiten utilitzar l'esound o alguna versió d'esound. Has provat l'esound?

Utilitzant l'Alsaconfig altra vegada podríes arreglar el problema.

..........
Potser necessites utlitzar alsaconfig al CLI". (Aixó si que no sé que vol dir)


Aclarit: el CLI es refereix a a utilitzar-lo desde el terminal

---

### Post by lo gambusí on 2009-04-11
I com faig anar *l'alsaconfig per la terminal*? :?

---

### Post by lo gambusí on 2009-04-11
Ja ho he solucionat, tenia el PCM-2 de l'OSS Mixer sense volum.

Gràcies igualment!

---

### Post by torracastanyes on 2009-04-11
En portuguès, "Moito Obrigado"

---

