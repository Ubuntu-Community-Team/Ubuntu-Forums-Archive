---
title: "Video and sound card installation ??"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by kmreleaser on 2008-02-12
hi everyone,

I've already installed Ubuntu to my PC, When I was installing the software I was not connected to the internet and i think that's why my video and sound card do not seem to be responding to anything, is there anyway like updating or something that allows me to have them to work? 

Not. I don't have the installation CDs neither know what kind of cards are they .. It's my machine at work :)

Thank you so much

---

### Post by pedro_orange on 2008-02-12
You should really try to find out what the hardware of your machine is, to ensure you are using the right kind of driver. 

If it's a Dell machine (like most work PCs are), they usually have a code somewhere on the box/laptop which you can punch into dell's website and it tells you whats inside. 
If it's not a Dell machine, you can still look up the machine at the vendors website. 

Once you have the hardware spec you can start looking for other Ubuntu users that have that hardware working (or not) for them, and how they did it.

If you have an nVidia/ATI graphics card, consider using Envy to install/configure your graphics settings.

Good luck

---

### Post by kpkeerthi on 2008-02-12
You do not have to be connected to the internet for your hardwares to work. Open a terminal and type ```
lspci
``` and post the output here. 

PS: Use [code] tags to post the output

---

### Post by kmreleaser on 2008-02-12
that's what I got:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)


Thanks

---

### Post by jan quark on 2008-02-12
you can also check if there are any inactive drivers going to
system > administration > restricted drivers manager

usually the graphic and network drivers are listed there

---

### Post by spiderbatdad on 2008-02-12
You will not have access to the restricted drivers until you get a working internet connection. You will then need to repair your sources.list [http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)
Then any restricted drivers will appear.

---

