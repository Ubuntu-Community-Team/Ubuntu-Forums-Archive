---
title: "Problemes inalàmbrics"
date: 2007-06-11
forum: Catalan Team
---

### Post by pepfabra on 2007-06-11
Hola!

No cal dir, que sóc novell en això de l'Ubuntu. He recuperat un portàtil de la primera època i sobre disc dur net l'he instal·lat. Tot correcte, però no aconsegueixo connectar-me a internet.
Al poble, tenim wifi gratuit. Amb windows xp, sense configurar res, ho reconeix, sense problemes. 
L'ordi és un hp compaq i la tarja inalàmbrica (que la reconeix quan arrenca) és una      . També he recuperat la D-link DWL-G122 usb 2.0 de l'ordinador de sobretaula (també la reconeix), i no hi ha manera!
Penseu que no en sé gaire de tot això, agrairia algun tipus d'ajuda, que no fos gaire complicada d'entendre. Per a “rucs]”, diguem-ne. Això sí, per a “rucs”, però catalans, eh?!!!:)

Gràcies i Salut!

---

### Post by pepfabra on 2007-06-11
Hola, de bell nou!

Amb tant de "ruc", m'he oblidat el nom de la primera tarja, Ha! Ha!
És una Broadcom Corporation Dell Wireless 1390 WLAN Mini-Pci Card.

Gràcies, i perdoneu!

---

### Post by patrickfromspain on 2007-06-11
en un terminal, posa:

lspci i lsusb y donans la sortida, amb les 2 tarjes instalades. Llavors igual veiem quin chip te la tarja i com es pot fer funcionar.

Salut!

---

### Post by pepfabra on 2007-06-11
pep@hpportatil:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01) 
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) 
pep@hpportatil:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 07d1:3c03 D-Link System 
Bus 003 Device 001: ID 0000:0000 


És això?

---

### Post by patrickfromspain on 2007-06-12
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Aixo es la teva tarjeta integrada al portatil. Hi ha un howto en aquesta web, en angles:

[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390)

A vere si et serveix

---

### Post by pepfabra on 2007-06-12
Gràcies, per la resposta. Ho intento malgrat els meus coneixements d'anglès, venen a ser com els que tinc sobre conexions inalàmbriques, en linux.:D

---

