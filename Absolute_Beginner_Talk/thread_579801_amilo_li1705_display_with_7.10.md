---
title: "amilo li1705 display with 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mikerobertso_UK on 2007-10-18
hi i can 7.04 to work ok on my amilo li1705 but the display can only do 600 x 800 which for me is not a big deal.Ive tried to put 7.10 on the laptop today but the display is blank any ideas the display working as how to get ?

many thanks in advance

---

### Post by overdrank on 2007-10-18
> **mikerobertso_UK said:**
> hi i can 7.04 to work ok on my amilo li1705 but the display can only do 600 x 800 which for me is not a big deal.Ive tried to put 7.10 on the laptop today but the display is blank any ideas the display working as how to get ?

many thanks in advance

HI it would help if you could give us some specs on the system.  please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help. 
Also this link may help with the resolution in 7.04
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by mikerobertso_UK on 2007-10-18
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6364
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:01.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
ubuntu@ubuntu:~$

---

### Post by overdrank on 2007-10-18
It appears you need to update the pci ids  with this comand
```
sudo update-pciids
```

---

### Post by mikerobertso_UK on 2007-10-18
ubuntu@ubuntu:~$ sudo update-pciids
--18:23:01--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 127,821 (125K) [text/plain]

 0% [                                     ] 0             --.--K/s             


Cannot write to `pci.ids.bz2' (No space left on device).
update-pciids: download failed
ubuntu@ubuntu:~$ 

this is what i get please fogive me i dont know what any of this means

---

### Post by overdrank on 2007-10-18
> **mikerobertso_UK said:**
> ubuntu@ubuntu:~$ sudo update-pciids
--18:23:01--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 127,821 (125K) [text/plain]

 0% [                                     ] 0             --.--K/s             


Cannot write to `pci.ids.bz2' (No space left on device).
update-pciids: download failed
ubuntu@ubuntu:~$ 

this is what i get please fogive me i dont know what any of this means

Ok, I assume we are working with feisty? The servers are overwhelmed I would assume.
Did you try and start the Gutsy live cd in safe graphics mode?

---

### Post by mikerobertso_UK on 2007-10-18
yes im working with feisty on a live cd before i install been using it for 2 days and i can im very imprssed indeed but i want to make sure everything will work when i put it on to the hdd as i am planing on using it instead of vista.

---

### Post by overdrank on 2007-10-18
> **mikerobertso_UK said:**
> yes im working with feisty on a live cd before i install been using it for 2 days and i can im very imprssed indeed but i want to make sure everything will work when i put it on to the hdd as i am planing on using it instead of vista.

Ok that explains the error then. If your system is like the one I found on the web it is using the unichrome graphics which is not really supported but does work with the vesa drivers.

---

### Post by mikerobertso_UK on 2007-10-18
vesa drivers where could i find these please?

---

### Post by overdrank on 2007-10-18
> **mikerobertso_UK said:**
> vesa drivers where could i find these please?

Hi if you are using the live cd then that is more than likely the driver being used. If you are trying to boot to the 7.10 live cd then you may want to choose safe graphics mode.

---

### Post by mikerobertso_UK on 2007-10-18
tried booting 7.10 in safe graphic mode but still a blank screen:(

---

### Post by overdrank on 2007-10-18
> **mikerobertso_UK said:**
> tried booting 7.10 in safe graphic mode but still a blank screen:(

Ok just to make sure did you check the cd for errors and also may want to checksum on the cd as well.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

---

### Post by MCkey on 2007-10-21
i have the same problem like mikerobertso_UK has about gutsy live cd.
everything is correct about the version, i checked, and i tried with the alternate version too... the result was the same... blank screen.
please, i need some help.

i know that the problem is with the graphic card, but is there a solution?

(Fu-Si Amilo Li 1705 - VIA Chrome9 HC IGP)

---

### Post by Orvar on 2007-10-28
The same here, using a CD that works perfectly on other computers. With the Fujitsu Siemens Li1705 the screen gets blank after initial text-mode. The "wait" symbol followed by the X windows symbol show up momentarily every 17-18 seconds, followed by what could be a very scrambled text message and a few seconds later a "flash" on the screen. Then nothing untill the next wait/X. 
Tried lots of things: different resolution (F4) settings, different languages, safe graphics mod, safe graphics mode + correct resolution (1280x800 using F4 at startup)... Nothing seems to work.
Maybe the X windows system doesn´t work with the VIA Chrome9 HC graphics?

---

### Post by squil on 2007-10-31
Unichrome p4m900 is not yet fully supported under linux.  There is however a branch of openchrome working on this : [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=P4M900](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=P4M900)
For me the compilation went okay but i got some strange behavior with this driver (disappearing mouse pointer, black spots on the screen, etc)

You can also try the official via driver by following the instructions given in this document : [http://www.viaarena.com/Driver/via_unichrome_fbd_v2.6.00.03a_appnote_ver0.8a.gz](http://www.viaarena.com/Driver/via_unichrome_fbd_v2.6.00.03a_appnote_ver0.8a.gz)

I did not manage to compile the official Via driver so I finally keep using the standard vesa driver.

To get the 1280x800 resolution, just do 
sudo dpkg-reconfigure xserver-xorg
Follow the steps, and choose the right resolution.

I never tried the gutsy live cd, but the feisty one worked fine for me on the amilo li1705...

mikerobertso_UK >>  Could you get your headphone jack to work?  That's something i never achieved with this laptop

---

### Post by mikerobertso_UK on 2007-12-03
no i gave up with ubuntu in the end which is a shame

---

### Post by MalleRIM on 2008-02-02
Hi,
how exactly did you manage openchrome to work, squil? I've got a laptop with Chrome9 HC IGP card and p4m900-chipset. I've been working on it for ages but I don't get anything to work. The gparted LiveCD works almost fine (the xserver has the right resolution). But nothing on Ubuntu. Ubuntus own drivers don't work, vias driver does not compile and openchrome does not work either. The only thing I got working was a mouse shown with correct sollution, followed by an xserver crash
Please help me

---

### Post by MalleRIM on 2008-02-03
I almost did it! There are just some artifacts but the resolution works!
Can someone please post his /etc/X11/xorg.conf for comparison?

---

### Post by squil on 2008-02-17
Hey, 
I put my xorg.conf over there : [http://www.sqnet.org/xorg.conf](http://www.sqnet.org/xorg.conf)
This is the configuration with the vesa driver.   For the openchrome driver you just have to change vesa by openchrome in the display section.  But as i said before i had some small bugs with the openchrome driver.

---

