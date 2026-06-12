---
title: "No detecta D-Link DWL-G510"
date: 2009-04-08
forum: Catalan Team
---

### Post by pobletex on 2009-04-08
Bones a tothom!

El meu problema és semblant a d'altres ja postejats però tot i utilitzar-ne les indicacions donades en altres posts no he acabat de resoldre-ho.

Les característiques són:

Tarjeta per wifi D-Link DWL-G510 ver.5.11 (E)- compatible amb linux
Kubuntu 8.10

He instal·lat el ndiswrapper i el ndisgtk. Tinc els drivers instal·lats però no em reconeix la tarjeta, em diu que no hi ha hardware. Òbviament, no em detecta wireless. Fent escanneig, també des de la consola, tampoc em detecta la tarjeta (ara no recordo amb quina ordre). I per a que pogueu veure una mica més:

:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)                                                                               
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


I:

:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:2a:5f:81
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  ***-network DISABLED**
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:cb:77:a3:08:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


He mirat moltes pàgines i indicacions i no me n'he sortit. Només he pogut arribar a tenir els drivers instal·lats. No sé si faig alguna cosa malament o és que no hi ha res a fer (en teoria és compatible amb linux).

Moltes gràcies. I espero que me'n pugui sortir ara que he decidit fer el salt definitiu a ubuntu, aquesta vegada sense particions amb windows... els meus últims problemes amb el windows xp sp3 i posteriors errors en el disc dur, i impossibilitat per arrencar (vegi's pantalles blaves, impossibilitat de fer un system32/restore...) m'han saturat del tot.

---

### Post by torracastanyes on 2009-04-08
No entenc perquè vols l'ndiswrapper.

Has provat el driver nadiu?.

De tota manera, el fet que no detecti el dispositiu és força sospitós. Prova de treure'l i tornar-lo a muntar. Algún cop m'he trobat que alguna peça topa amb la carcassa de l'ordinador i els connectors no arriben a fer contacte.

---

### Post by pobletex on 2009-04-09
> **torracastanyes said:**
> No entenc perquè vols l'ndiswrapper.

Has provat el driver nadiu?.

De tota manera, el fet que no detecti el dispositiu és força sospitós. Prova de treure'l i tornar-lo a muntar. Algún cop m'he trobat que alguna peça topa amb la carcassa de l'ordinador i els connectors no arriben a fer contacte.

Al principi, mirant webs pensava que el ndiswrapper serviria pel meu cas i sí, ho he fet amb el driver propi de la tarjeta (xxxx.inf i xxxx.sys) si et refereixes a això.
I.... ara sí que em detecta el hardware, déu ni do!! Després de fer lspci,a l'última línia ja surt el "network controller". Però ara no em detecta la meva xarxa sinó una altra. I estic a l'habitació del costat del router! Seguiré mirant informació als fòrums que segurament això ha passat a més gent.
Bé, de moment, la cosa ha anat més bé i ràpida del que m'esperava. Segona part!

---

### Post by pobletex on 2009-04-09
Increïble!!!! Estava mirant altres fils amb temes com assegurat que no tingui botó d'arrencada la tarjeta de xarxa, que si iwconfig i la sortida que dóna per ESSID, treure la protecció del router, etc. I torno a mirar i ja m'ha trobat la meva xarxa i m'hi he pogut connectar, tot i que no al 100% tota l'estona.

Bé, gràcies per les molèsties. En principi el marcaré com a Solved, a veure si durant el dia no em dóna cap ensurt.

---

### Post by torracastanyes on 2009-04-09
L'Ndiswrapper serveix per instalar drivers de windows quant no n'hi ha d'altres, el que et preguntava es si ja has provat el driver nadiu per a linux, que n'hi ha:

[http://www.dlinkla.com/home/productos/producto.jsp?idp=716](http://www.dlinkla.com/home/productos/producto.jsp?idp=716)

Si ja detecta alguna xarxa, vol dir que la tarja funciona, si no veu la teva, mira si el router té seleccionada la ESSID pública.

Editat: Perdona, estava escrivint i no he vist la teva resposta. M'alegro que ho hagis solucionat.

---

### Post by pobletex on 2009-04-09
Ja em perdonareu aquest extra. Volia marcar el fil com a sol·lucionat però en Thread Tools no em surt l'opció de marca'l com a solved.

---

### Post by SiscoGarcia on 2009-04-09
> **pobletex said:**
> Ja em perdonareu aquest extra. Volia marcar el fil com a sol·lucionat però en Thread Tools no em surt l'opció de marca'l com a solved.

De moment això no és possible, fa un temps que en vam parlar aquí al fòrum, tret que tornin a fer un maquillatge nou i ho tornin a incorporar.

---

