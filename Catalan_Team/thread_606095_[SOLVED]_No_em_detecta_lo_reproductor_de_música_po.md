---
title: "[SOLVED] No em detecta lo reproductor de música portàtil (Samsung YP-U3)"
date: 2007-11-07
forum: Catalan Team
---

### Post by lo gambusí on 2007-11-07
Avui he comprat un reproductor de música portàtil Samsung YP-U3:

[IMG]http://xataka.com/images/2007/06/samsungypu3-0.jpg[/IMG]

He comprat este perquè tot i ser una mica més car que los altres, té suport ogg vorbis, i vull intentar dependre lo mínim possible de formats privatius.

Lo cas és que lo poso a l'entrada USB i s'il·lumina la pantalla del reproductor, em diu que s'està connectant, que s'ha connectat i finalment es dedica a carregar la bateria. A l'ordinador, però no me dona cap mena de senyal:-?

He mirat per internet a vore si trobava algú que li hagués passat lo mateix i tal, però no he trobat res.

Creieu que pot ser incompatible en Ubuntu lo reproductor? Seria realment un poc suc que sigue capaç de llegir ogg i que no sigue compatible en un S.O. lliure...:mad:

Alguna idea?

---

### Post by papapep on 2007-11-07
> Lo cas és que lo poso a l'entrada USB i s'il·lumina la pantalla del reproductor, em diu que s'està connectant, que s'ha connectat i finalment es dedica a carregar la bateria. A l'ordinador, però no me dona cap mena de senyal


Que se suposa que ha de fer l'ordinador solet??? :-D

En teoria, programes com l'Amarok han de poder connectar amb aquest dispositiu i intercanviar fitxers amb ell. El tens instal·lat? Igual també et funcionarien el Listen o el Shoutbox, però com que no els conec doncs no t'ho asseguro.

---

### Post by lo gambusí on 2007-11-07
En lo llapis usb i en l'antic reproductor que tenia, quan los connectava se m'obria la carpeta en los arxius, per posar-ne, treure'n i lo que fes falta. 

I no,l'Amarok no me'l detecta tampoc... :(

---

### Post by lluisanunez on 2007-11-07
Mira't aquest fil en anglès:
[http://ubuntuforums.org/showthread.php?t=540577&highlight=samsung+mp3+player](http://ubuntuforums.org/showthread.php?t=540577&highlight=samsung+mp3+player)
on es proposen diverses solucions, però la del darrer post sembla que és la que funciona

---

### Post by lo gambusí on 2007-11-07
Me perdo una mica en l'explicació. He fet lo que me demana al codi i me surt igual que a ells. Però a l'hora d'editar l'arxiu i afegir-hi lo que me diu, me surt un error que diu */etc/udev/rules.d és un directori.Comproveu que la ubicació estigui ben escrita i torneu-ho a intentar.*

Tens idea què puc fer ara? No sé si és perquè no entenc bé l'anglès o perquè directament no entenc l'explicació... :(

---

### Post by papapep on 2007-11-07
Gambusí, t'has d'explicar una mica més detalladament, concretant quines ordres has fet i amb quina et surt el missatge aquest.

---

### Post by papapep on 2007-11-07
A veure, a la pàgina orígen del mètode que has seguit, posa:

>    1. vérifiez que les paquets suivants sont bien installés :
         1. udev
         2. usbutils
         3. libmtp5
   2. connectez la clé
   3. vérifiez qu'elle est reconnue :
      mickael@zulio:~$ lsusb
      Bus 005 Device 005: ID 04e8:507d Samsung Electronics Co., Ltd
   4. déconnectez la clé
   5. ouvrir le fichier /etc/udev/rules.d/65-libmtp.rules et ajoutez la ligne suivante :
      # Samsung YP-U3 (YP-U3)
      SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="666"
   6. redémarrez udev :
      sudo /etc/init.d/udev restart


 
Aleshores, suposant que tinguis els paquets del primer punt instal·lats, (sinó els tens "sudo aptitude install udev usbutils libmtp5") i que fent el lsusb et surt el que posa al punt 2, amb l'ordre:

```
sudo nano /etc/udev/rules.d/65-libmtp.rules
```

hauries de poder afegir les dues línies que especifica

Recorda desconnectar el dispositiu de l'ordinador abans de fer els punts 5 i 6.

---

### Post by lo gambusí on 2007-11-07
Tens raó, sempre peco del mateix mal...

Mira, he anat seguint les indicacions que diu a la web que m'ha enllaçat.

He obert la consola sense l'mp3 posat i li he dit (i m'ha respost):

> oriol@oriol-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:0896 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


Llavors he posat l'mp3 a l'ordinador i li he dit lo mateix;
> oriol@oriol-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 04e8:507d Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 046d:0896 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


Després he dit > oriol@oriol-laptop:~$ tail -n 100 /var/log/messages
 i m'ha respost > Nov  7 23:16:32 oriol-laptop kernel: [    7.416000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.3-1
Nov  7 23:16:32 oriol-laptop kernel: [    7.416000] usbcore: registered new interface driver usbhid
Nov  7 23:16:32 oriol-laptop kernel: [    7.416000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov  7 23:16:32 oriol-laptop kernel: [    7.928000] kjournald starting.  Commit interval 5 seconds
Nov  7 23:16:32 oriol-laptop kernel: [    7.932000] EXT3-fs: recovery complete.
Nov  7 23:16:32 oriol-laptop kernel: [    7.940000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  7 23:16:32 oriol-laptop kernel: [   16.824000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  7 23:16:32 oriol-laptop kernel: [   16.836000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  7 23:16:32 oriol-laptop kernel: [   16.972000] iTCO_vendor_support: vendor-support=0
Nov  7 23:16:32 oriol-laptop kernel: [   16.988000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  7 23:16:32 oriol-laptop kernel: [   16.988000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Nov  7 23:16:32 oriol-laptop kernel: [   16.988000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  7 23:16:32 oriol-laptop kernel: [   17.248000] Linux agpgart interface v0.102 (c) Dave Jones
Nov  7 23:16:32 oriol-laptop kernel: [   17.632000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov  7 23:16:32 oriol-laptop kernel: [   17.632000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov  7 23:16:32 oriol-laptop kernel: [   17.700000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
Nov  7 23:16:32 oriol-laptop kernel: [   17.732000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Nov  7 23:16:32 oriol-laptop kernel: [   17.788000] Yenta: CardBus bridge found at 0000:06:04.0 [1025:0090]
Nov  7 23:16:32 oriol-laptop kernel: [   17.788000] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov  7 23:16:32 oriol-laptop kernel: [   17.788000] Yenta: Routing CardBus interrupts to PCI
Nov  7 23:16:32 oriol-laptop kernel: [   17.788000] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
Nov  7 23:16:32 oriol-laptop kernel: [   17.816000] sdhci: Secure Digital Host Controller Interface driver
Nov  7 23:16:32 oriol-laptop kernel: [   17.816000] sdhci: Copyright(c) Pierre Ossman
Nov  7 23:16:32 oriol-laptop kernel: [   17.912000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Nov  7 23:16:32 oriol-laptop kernel: [   17.912000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Nov  7 23:16:32 oriol-laptop kernel: [   17.936000] nvidia: module license 'NVIDIA' taints kernel.
Nov  7 23:16:32 oriol-laptop kernel: [   18.196000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Nov  7 23:16:32 oriol-laptop kernel: [   18.196000] Socket status: 30000006
Nov  7 23:16:32 oriol-laptop kernel: [   18.196000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Nov  7 23:16:32 oriol-laptop kernel: [   18.196000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Nov  7 23:16:32 oriol-laptop kernel: [   18.196000] cs: IO port probe 0x2000-0x2fff: clean.
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] pcmcia: parent PCI bridge Memory window: 0xd2000000 - 0xd20fffff
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] PCI: Enabling device 0000:06:04.2 (0000 -> 0002)
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 17
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] mmc0: SDHCI at 0xd2003400 irq 17 DMA
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] sdhci: SDHCI controller found at 0000:06:04.4 [1524:0551] (rev 1)
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] PCI: Enabling device 0000:06:04.4 (0000 -> 0002)
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] ACPI: PCI Interrupt 0000:06:04.4[B] -> GSI 17 (level, low) -> IRQ 17
Nov  7 23:16:32 oriol-laptop kernel: [   18.200000] mmc1: SDHCI at 0xd2003100 irq 17 PIO
Nov  7 23:16:32 oriol-laptop kernel: [   18.216000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Nov  7 23:16:32 oriol-laptop kernel: [   18.224000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Nov  7 23:16:32 oriol-laptop kernel: [   18.336000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  7 23:16:32 oriol-laptop kernel: [   18.336000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Nov  7 23:16:32 oriol-laptop kernel: [   18.340000] Linux video capture interface: v2.00
Nov  7 23:16:32 oriol-laptop kernel: [   18.448000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Nov  7 23:16:32 oriol-laptop kernel: [   18.632000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Nov  7 23:16:32 oriol-laptop kernel: [   18.676000] usbcore: registered new interface driver gspca
Nov  7 23:16:32 oriol-laptop kernel: [   18.676000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Nov  7 23:16:32 oriol-laptop kernel: [   18.756000] cs: IO port probe 0x100-0x3af: clean.
Nov  7 23:16:32 oriol-laptop kernel: [   18.756000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Nov  7 23:16:32 oriol-laptop kernel: [   18.756000] cs: IO port probe 0x820-0x8ff: clean.
Nov  7 23:16:32 oriol-laptop kernel: [   18.756000] cs: IO port probe 0xc00-0xcf7: clean.
Nov  7 23:16:32 oriol-laptop kernel: [   18.760000] cs: IO port probe 0xa00-0xaff: clean.
Nov  7 23:16:32 oriol-laptop kernel: [   19.912000] hda_intel: azx_get_response timeout, switching to polling mode...
Nov  7 23:16:32 oriol-laptop kernel: [   20.148000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Nov  7 23:16:32 oriol-laptop kernel: [   20.256000] lp: driver loaded but no devices found
Nov  7 23:16:32 oriol-laptop kernel: [   20.404000] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
Nov  7 23:16:32 oriol-laptop kernel: [   20.872000] EXT3 FS on sda1, internal journal
Nov  7 23:16:32 oriol-laptop kernel: [   21.968000] NET: Registered protocol family 17
Nov  7 23:16:32 oriol-laptop kernel: [   22.192000] ACPI: AC Adapter [ACAD] (on-line)
Nov  7 23:16:32 oriol-laptop kernel: [   22.412000] ACPI: Battery Slot [BAT1] (battery present)
Nov  7 23:16:32 oriol-laptop kernel: [   22.436000] No dock devices found.
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] input: Power Button (FF) as /class/input/input4
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] ACPI: Power Button (FF) [PWRF]
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] input: Lid Switch as /class/input/input5
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] ACPI: Lid Switch [LID]
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] input: Sleep Button (CM) as /class/input/input6
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] ACPI: Sleep Button (CM) [SLPB]
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] input: Power Button (CM) as /class/input/input7
Nov  7 23:16:32 oriol-laptop kernel: [   22.496000] ACPI: Power Button (CM) [PWRB]
Nov  7 23:16:32 oriol-laptop kernel: [   22.724000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov  7 23:16:32 oriol-laptop kernel: [   22.724000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Nov  7 23:16:35 oriol-laptop kernel: [   26.248000] ppdev: user-space parallel port driver
Nov  7 23:16:35 oriol-laptop kernel: [   26.660000] audit(1194473795.498:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5260 profile="/usr/sbin/cupsd"
Nov  7 23:16:35 oriol-laptop kernel: [   26.764000] apm: BIOS not found.
Nov  7 23:16:39 oriol-laptop kernel: [   30.760000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Nov  7 23:16:40 oriol-laptop kernel: [   31.972000] Failure registering capabilities with primary security module.
Nov  7 23:16:41 oriol-laptop dhcdbd: Started up.
Nov  7 23:16:48 oriol-laptop kernel: [   39.364000] NET: Registered protocol family 10
Nov  7 23:16:48 oriol-laptop kernel: [   39.364000] lo: Disabled Privacy Extensions
Nov  7 23:16:48 oriol-laptop kernel: [   39.364000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  7 23:18:55 oriol-laptop kernel: [  166.920000] usb 1-3: USB disconnect, address 2
Nov  7 23:20:09 oriol-laptop kernel: [  240.096000] usb 1-1: new high speed USB device using ehci_hcd and address 5
Nov  7 23:20:09 oriol-laptop kernel: [  240.228000] usb 1-1: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
Nov  7 23:20:09 oriol-laptop kernel: [  240.228000] usb 1-1: configuration #1 chosen from 1 choice
Nov  7 23:21:46 oriol-laptop kernel: [  337.404000] UDF-fs: No VRS found
Nov  7 23:32:03 oriol-laptop kernel: [  954.784000] usb 1-1: USB disconnect, address 5
Nov  7 23:32:09 oriol-laptop kernel: [  960.168000] usb 1-1: new high speed USB device using ehci_hcd and address 6
Nov  7 23:32:09 oriol-laptop kernel: [  960.300000] usb 1-1: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
Nov  7 23:32:09 oriol-laptop kernel: [  960.300000] usb 1-1: configuration #1 chosen from 1 choice
Nov  7 23:53:59 oriol-laptop kernel: [ 2270.400000] usb 1-1: USB disconnect, address 6
Nov  7 23:54:03 oriol-laptop kernel: [ 2274.860000] usb 1-1: new high speed USB device using ehci_hcd and address 7
Nov  7 23:54:03 oriol-laptop kernel: [ 2274.992000] usb 1-1: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
Nov  7 23:54:03 oriol-laptop kernel: [ 2274.992000] usb 1-1: configuration #1 chosen from 1 choice
Nov  8 00:13:42 oriol-laptop kernel: [ 3453.292000] usb 1-1: USB disconnect, address 7
Nov  8 00:13:57 oriol-laptop kernel: [ 3468.716000] usb 1-1: new high speed USB device using ehci_hcd and address 8
Nov  8 00:13:57 oriol-laptop kernel: [ 3468.848000] usb 1-1: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
Nov  8 00:13:57 oriol-laptop kernel: [ 3468.848000] usb 1-1: configuration #1 chosen from 1 choice


Ara hauria de dir-li > /etc/udev/rules.d per editar, però me diu que este fitxer és un directori i lo que he posat en cursiva a l'intervenció anterior.

---

### Post by lo gambusí on 2007-11-07
Ui, anem per parts que hem respost los dos alhora. Miro això que m'has dit.;)

---

### Post by papapep on 2007-11-07
Fes el que t'he posat just abans de la teva resposta última i veuràs com va millor el tema ;-)

---

### Post by lo gambusí on 2007-11-07
Molt bé, ara he instal·lat lo programa i ja me dixa fer-ho!!

Passa que pel que veig he d'anar de cançó en cançó, pel que me puc morir... :(

però bé, ja és alguna cosa!

moltes gràcies a tots dos!:D

alguna idea de per què ha passat això?

---

### Post by papapep on 2007-11-07
La resposta és mooooolt fàcil: perquè els fabricants només es preocupen de que les coses funcionin (i ni això solen fer bé) en un sól sistema operatiu.

La resta de mortals ens hem de escarrassar en trobar sol·lucions i fer dreceres per fer funcionar les coses.

---

### Post by lo gambusí on 2007-11-07
Malgrat tot, la sensació de satisfacció d'haver-te'n sortit (encara que gràcies a altres persones) paga la pena, no creus? :)

---

### Post by papapep on 2007-11-08
Evidentment. És una sensació molt gratificant. El fet de poder solucionar, tu mateix o amb l'ajut d'altres, la immensa majoria de problemes, és un dels punts forts d'el plantejament de Linux. (com a mínim així ho veig jo, vaja)

---

### Post by lluisanunez on 2007-11-08
> **lo gambusí said:**
> Malgrat tot, la sensació de satisfacció d'haver-te'n sortit (encara que gràcies a altres persones) paga la pena, no creus? :)

Tens raó! això és el millor. 
Aquest estiu em vaig comprar el mòdem 3G per poder tenir ample de banda allà al meu poble. Entro a can Vodafone i pregunto sobre preus, etc., i finalment pregunto el model i marca del mòdem i les dades de configuració (lloc, usuari i contrasenya). Em contesten:
- No, no et cal tot això, fiques el mòdem i es configura tot sol al Windows
- Ah, però és que jo no tinc Windows, tinc Linux
El comercial es posa pà&#320;lid i diu que ell és **de lletres(!!!)** i que no em pot ajudar, però allà mateix té un PC connectat a Internet, li demano, entro al fòrum d'Ubuntu i busco el model i marca del mòdem. Trobo uns quants fils amb el [SOLVED], me'ls miro per sobre i veig que ja me'l puc comprar que l'aconseguiré fer funcionar. El comercial mirava amb la boca oberta. Li dic:
- Veus? no és qüestió de lletres ni ciències, sinó de tenir molts amics que comparteixen el que saben. I em diu:
- M'has convençut! per fi em podré alliberar del Windows que no m'agrada gens!
:-D

---

### Post by CarlesOriol on 2007-11-09
:-D Genial

---

### Post by lo gambusí on 2008-08-28
Sento pujar un tema ja resolt i antic, però m'he trobat amb una cosa ben estranya.

El reproductor portàtil, que ja fa temps que em funcionava de meravella, de cop i volta no és reconegut pel programa, el gnomad2 este. Quan l'obro el primer missatge que hem dóna és que no detecta cap reproductor connectat.

He fet l'lsusb i sí apareix, he reinstal·lat el gnomad2 i segueix igual. Alguna idea de què puc fer, i per què deu haver-me passat, això?

Gràcies!

---

### Post by lluisanunez on 2008-08-29
Mira si t'està muntant el reproductor tal com el programa s'espera trobar-lo (preferències). A mi em sortia un missatge semblant i la diferència era /media/ipod en comptes de /media/IPOD

---

### Post by lo gambusí on 2008-08-29
Però és que l'ubuntu no em detecta el reproductor (mai no ho ha fet, sempre me l'ha reconegut només el programa).

Les preferències del programa no m'aclarixen [gaire cosa...]("http://img142.imageshack.us/img142/1981/capturayh1.png")

---

### Post by lo gambusí on 2008-08-30
Cap proposta?

---

### Post by papapep on 2008-08-30
Has verificat que [tens instal·lats els paquets]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/131744") [libmtp-dev]("http://packages.ubuntu.com/hardy/libmtp-dev") i [libmtp7]("http://packages.ubuntu.com/hardy/libmtp7") ?:

---

### Post by lo gambusí on 2008-08-30
Pos lo libmtp-dev no'l tenia instal·lat. Però no hi ha hagut cap canvi visible, seguix sense localitzar-me lo reproductor...

---

### Post by papapep on 2008-08-30
I l'Amarok, has provat si el detecta?? aquest ho enganxa gairebé tot...

Per cert, en fer un lsusb, què hi surt?

---

### Post by lo gambusí on 2008-08-30
L'amarok mai no me l'ha detectat, ni quan em funcionava el Gnomad2

I l'lsusb si m'ho detecta, mira:
> us 005 Device 002: ID 046d:0896 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

---

### Post by papapep on 2008-08-30
Crec que el lsusb no te'l detecta. Entenc que hauria de sortir-te una línia semblant a això:

```
Bus 001 Device 003: ID 04e8:507f Samsung Electronics Co., Ltd
```

a l'enllaç que t'he posat abans posava que, a partir de la versió per a Gutsy, les llibreries mtp ja portaven suport pel teu aparell. És curiós el teu problema...
Has provat a algun altre port usb del teu ordinador?? jo m'havia trobat, temps enrera, que no tots els ports de l'ordinador anaven igual de bé...
És per eliminar possibilitats, saps?

---

### Post by lo gambusí on 2008-08-30
Si, ja ho he provat i segueix sense detectar-me'l... :?

A més hi ha una altra cosa estranya, que me fa sospitar que no sigue lo meu reproductor... Ans quan posava l'aparell al lector s'il·luminava i es posava a carregar... i ara no fa res :|

Edito: he provat a vore si lo gnomad2 me llig un llapis usb i no me'l llig. Ara, no sé si normalment los llig o no...

---

### Post by papapep on 2008-08-31
> Ans quan posava l'aparell al lector s'il·luminava i es posava a carregar... i ara no fa res 

Clar, doncs això flaire malament....
Hauries de verificar que funciona bé, o no, a algun altre ordinador, abans de seguir-nos escarrassant amb el tema, oi? :-)

---

### Post by lo gambusí on 2008-08-31
És lo que vaig pensar anit. Ara que vaig a la biblioteca ho miraré i us dic alguna cosa.

---

### Post by lo gambusí on 2008-08-31
Què bé, no me'l detecta ni un MAC ni un PC en windows... així que probablement estigue fet malbé. :(:mad::???::cry:

Lo mal és que funcionar funciona, per tant suposo que s'haurà trencat l'usb o què sé jo... per tant estic sense manera de carregar-li la bateria i canviar-li la música. 

Gràcies per tot, papapep.

PS: Sabeu d'algun reproductor de música que suporti OGG VORBIS bé de preu? :lolflag:

---

### Post by papapep on 2008-08-31
Algun d'aquests sembla que reprodueix ogg sense problemes:

 - [http://www.iriver.eu.com/buy_product.html?L=3](http://www.iriver.eu.com/buy_product.html?L=3)

 i els teus "estimats" Samsung :-) , i un Kingston  :

 - [http://www.optize.es/servlet/KINGSTON_K-PEX_100_-_RADIO___REPRODUCTOR_306313_optize.html](http://www.optize.es/servlet/KINGSTON_K-PEX_100_-_RADIO___REPRODUCTOR_306313_optize.html)
 - [http://www.optize.es/servlet/SAMSUNG_YP-T10JAW_-_RADIO___REPRODUCTOR__339029_optize.html](http://www.optize.es/servlet/SAMSUNG_YP-T10JAW_-_RADIO___REPRODUCTOR__339029_optize.html)
 - [http://www.optize.es/servlet/SAMSUNG_YP-T10JAB_-_RADIO___REPRODUCTOR__339028_optize.html](http://www.optize.es/servlet/SAMSUNG_YP-T10JAB_-_RADIO___REPRODUCTOR__339028_optize.html).

Respecte si són barats o cars, doncs això no ho sé...

---

### Post by lo gambusí on 2008-08-31
Moltes gràcies, ja aniré mirant... marco com a "solved":roll:

---

### Post by SiscoGarcia on 2008-08-31
> **lo gambusí said:**
> Sabeu d'algun reproductor de música que suporti OGG VORBIS bé de preu? :lolflag:

Per informació que no sigui ;) A més dels que ja t'ha passat el papapep, a la feina m'han deixat un [trekstor iBeat]("http://www.trekstor.de/es/products/detail_mp3.php?pid=19&cat=0") de 2 GB que funciona de meravella, i suporta ogg. No tinc ni idea del seu preu.

---

