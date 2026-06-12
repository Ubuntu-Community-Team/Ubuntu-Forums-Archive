---
title: "Connexió wifi lenta"
date: 2010-08-20
forum: Catalan Team
---

### Post by albertdelleida on 2010-08-20
Hola a tots i totes,

com prova l'estiu? Espero que molt bé. Des de l'últim post he gaudit de Ubuntu 10.04 i no m'ha donat cap tipus de problema. 

Ara bé, fa una setmana (aproximadament) he començat a tenir problemes amb la connexió wifi (de Telefonica). De cop i volta la connexió es talla, a vegades la velocitat és extremadament lenta (tarda estona en carregar qualsevol pàgina) i després torna a funcionar correctament.

En un principi vaig pensar que seria un problema de la pròpia Telefonica però em van comprovar la línia i funcionava perfectament. Llavors, vaig provar de connectar-me amb l'altre sistema operatiu que tinc instal·lat (windows vista) i també funciona perfectament. 

He estat buscant informació a la xarxa i pel que he vist els routers de la Telefonica poden portar alguns problemes amb Ubuntu però a mi no me n'havia donat mai cap ni un fins ara.

Algú em podria donar un cop de mà? Us ho agrairia molt ja que ara que estic acostumat a treballar amb Ubuntu no m'agrada haver d'obrir l'altre sistema operatiu només per navegar per Internet.

Espero les vostres respostes i moltes gràcies a totes i a tots :p

---

### Post by kukat on 2010-08-20
quins canvis ha tingut l'ordinador (programari, kernels...) abans de que començara a passar???

Pot provar amb altre kernel. Al GRUB, en lloc d'elegir el primer, elegeixes un altre kernel (si tens més d'un!)

Salutacions!

---

### Post by albertdelleida on 2010-08-20
de canvis no n'he fet cap d'important, simplement he anat instal·lant les actualitzacions que em recomanen. Com a fonts de programari tinc les de Ubuntu (main, universe, restricted i multiverse) i també les de [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner i Medibuntu - Ubuntu 10.04 "lucid lynx" (ambdues me les va recomanar algú en algun altre post). 

provaré d'entrar amb un altre kernel i us comento si continuen els problemes!

merci :)

---

### Post by kimet on 2010-08-20
Hauries de dir quina targeta wifi fas servir:

```
lspci
``` o ```
lsusb
``` en cas de que sigui usb.

---

### Post by albertdelleida on 2010-08-20
em surt això:

[I]00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0a:00.4 System peripheral: JMicron Technology Corp. xD Host Controller[/I]

:p

---

### Post by kimet on 2010-08-20
> 08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

:p

---

### Post by albertdelleida on 2010-08-23
Miraculosament, el problema s'ha arreglat sol :confused: potser sí que era un problema de la companyia d'ADSL. En tot cas, merci a tots per l'ajuda :)

---

