---
title: "Serious Beginner's Help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by callmemrwaffles on 2007-07-29
let me start off by saying i'm totally new to ubuntu. and i need some help.

1) how can i get ubuntu to work with my wireless internet connection? i'm using a wep hex password and it doesn't work even when i manually enter the settings.

2) how can i fix my screen resolution? i'm using a 15.4 inch widescreen, and i'd like my resolution to be in the same ratio.

3) a friend told me about wine, but i have no idea how to use it. help.

i hope someone can help me.

---

### Post by Vague on 2007-07-29
> **callmemrwaffles said:**
> 1) how can i get ubuntu to work with my wireless internet connection? i'm using a wep hex password and it doesn't work even when i manually enter the settings.

2) how can i fix my screen resolution? i'm using a 15.4 inch widescreen, and i'd like my resolution to be in the same ratio.

3) a friend told me about wine, but i have no idea how to use it. help.

i hope someone can help me.

Not sure on number 1 totally, but just as a guess, is the driver enabled in the restricted drivers manager?  In terms of number 2, if changing your display settings doesn't offer you the resolution you need, you may have to reconfigure your X server.  You can do this by going to the terminal and entering ```
sudo dpkg-reconfigure xserver-xorg
``` and selecting the resolution you'd like to run at.  Out of curiosity, what graphics card are you running, and do you have the proper driver for it installed?  In terms of 3, a bit of warning first.  If you're going to use Wine, you need to be pretty comfortable using the command line and doing a lot of tweaking.  Very few programs will do anything like "just working" in Wine.  You can check the Wine AppDB ([http://appdb.winehq.org/](http://appdb.winehq.org/)) for help with specific applications, or questions about how well they work with Wine.  What are you stuck on now?  Installing it or just using it?

---

### Post by callmemrwaffles on 2007-07-29
when i go to restricted drivers manager, it says i don't need any restricted drivers for my hardware

when i enter that code into terminal it asks me what driver to use: sisusb, tdfx, tga. trident, tseng, and vesa. which do i use?

and i already have wine installed, i was just wondering how to install a program i have on a cd

---

### Post by w4ett on 2007-07-29
From the terminal type:
```

lspci
```

This will let us know what chipsets and cards you are using.  Please post the results back here in the forum.

---

### Post by doodger on 2007-07-29
to install a program on a cd open a terminal and type

cd /media/cdrom0
this willl place you into the cd directory then enter
ls
wich will show you all the cd's files and folder. Just win the setup.exe it should work

 Hope it helped!

---

### Post by callmemrwaffles on 2007-07-29
alright here's what i get from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

and thanks doodger, it's working so far

---

### Post by ugm6hr on 2007-07-29
For the wifi issue:
[http://ubuntuforums.org/showpost.php?p=2857560&postcount=1](http://ubuntuforums.org/showpost.php?p=2857560&postcount=1)

---

### Post by w4ett on 2007-07-29
> **callmemrwaffles said:**
> 

when i enter that code into terminal it asks me what driver to use: sisusb, tdfx, tga. trident, tseng, and vesa. which do i use?




You will need to select the Intel driver

---

### Post by splintercellguy on 2007-07-29
> **callmemrwaffles said:**
> let me start off by saying i'm totally new to ubuntu. and i need some help.

1) how can i get ubuntu to work with my wireless internet connection? i'm using a wep hex password and it doesn't work even when i manually enter the settings.

2) how can i fix my screen resolution? i'm using a 15.4 inch widescreen, and i'd like my resolution to be in the same ratio.

3) a friend told me about wine, but i have no idea how to use it. help.

i hope someone can help me.

1. The responses before mine probably have the answer, but I would look for a restricted driver or use ndiswrapper.

2. As mentioned before, sudo dpkg-reconfigure xserver-xorg.

3. First off, following these instructions to get the latest latest Wine ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)), you would install it, then in a Terminal, type winecfg. This will create your Wine "Windows" folder. Then, if you want to try an app under Wine, consult the AppDb at the Wine website, and to start the installer/application, you would type wine "path to EXE".

---

