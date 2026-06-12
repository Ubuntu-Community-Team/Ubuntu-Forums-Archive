---
title: "Broadcom trouble"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-14
I just bought a Compaq Presario 410 (V5000) laptop and I can't figure out how to get the wireless card working.

'lspci' brings up this:

```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
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
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:08.0 Ethernet controller: Intel Corporation Unknown device 1092 (rev 01)
```

Someone said that I have a Broadcom 4301 (rev 01) card, but it looks like it says "Broadcom Corporation Unknown device 4311 (rev 01)" ...

Anyways, I tried this tutorial ([https://help.ubuntu.com/community/Wi...Driver/bcm43xx);](https://help.ubuntu.com/community/Wi...Driver/bcm43xx);) in the section 1.2.2.1. it says to download a driver and to extract the firmware parts. I downloaded bcmwl564.sys and extracted bcmwl564.sys and netbc564.inf . The tutorial then says to "install them to the correction location" and then goes on to the next section. I don't know what that's supposed to mean (ie - where do I install these things?)

So, I haven't had any luck so far, can someone please help? This kinda makes me mad 'cause I installed Fedora Core 5 on my laptop when I first got it and was going to have to use 'yum' and 'ndiswrapper' to set up the wireless card, well, that's what people on the Fedora forums told me. But my friend installed ubuntu onto his Gateway laptop and it recognized his card right away.

Oh, well... Any ideas????

---

### Post by John.Michael.Kane on 2006-09-14
I think you need the bcm43xx-firmware package section 1.2.2.2. Firmware Packages
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Also reading that guide it would seem that the way you did it was the frist method. the section i linked to i think is method two.

---

### Post by twade on 2006-09-14
As far as I know the bcm43xx solution does not yet work for bcm4311 cards.  I managed to get a bcm4311 to work on a compaq v3000 in 32 bit Ubuntu using the steps on this thread:
[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)
I believe the ndiswrapper that comes with Ubuntu doesn't work (I used version 1.23 which is still the current download version)  I tried using the drivers that came with my laptop - they didn't work, use the one in the link!  It may be neccessary to remove old attempts first (see the 5th post down)

---

### Post by mykrob on 2006-09-15
i have the same chipset in my Compaw V5204NR. You can do it using ndiswrapper. First, delete the ndiswrapper that comes with ubuntu. Go to ndiswrappers website and download the latest version, install from source..

You'll also need to install wine. Go to compaqs website and download the driver for your model laptop for the broadcom wifi chipset, and run the softpaq.exe with wine in the console like this

wine sp####.exe

it will extract the contents of the file to the current directory. Then, use ndiswrapper to load the .inf file you got from the softpaq..

If you need more details, post back, or send me a PM. but a quick search of the forums will show you details on using ndiswrapper.

-myk

---

### Post by nalioth on 2007-03-29
> **mykrob said:**
> i have the same chipset in my Compaw V5204NR. You can do it using ndiswrapper. First, delete the ndiswrapper that comes with ubuntu. Go to ndiswrappers website and download the latest version, install from source..

You'll also need to install wine. Go to compaqs website and download the driver for your model laptop for the broadcom wifi chipset, and run the softpaq.exe with wine in the console like this

wine sp####.exe

it will extract the contents of the file to the current directory. Then, use ndiswrapper to load the .inf file you got from the softpaq..

If you need more details, post back, or send me a PM. but a quick search of the forums will show you details on using ndiswrapper.

-myk  You do not need wine to install from this.  Use your package manager to install 'cabextract' and run it in a terminal against the sp####.exe and it will unpack all of the contents.

---

