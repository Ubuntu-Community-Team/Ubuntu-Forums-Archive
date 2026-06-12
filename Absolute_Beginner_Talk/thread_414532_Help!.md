---
title: "Help!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by papafred07 on 2007-04-19
After reading about Ubuntu for several months, I decided to take a chance and install it (I waited until today for the release of 7.04).  While I've managed to install it properly, I am encountering a couple problems.  First of all, my resolution is capped much lower than my screens res of 1440x900 (I am running on a Dell e1405 laptop).  Furthermore, I have had no success in establishing any sort of connection with my wireless network.  I had no luck connecting to either a friends unsecured network, or my secured one. any suggestions?  On another note, does anyone know if it is possible to sync my Microsoft Zune with Ubuntu?

thanks for the help!

Fred

---

### Post by lamalex on 2007-04-19
for the resolution, you'll need to edit something called the xorg.conf.

open a terminal and type this
```

sudo nano /etc/X11/xorg.conf

```
and add your desired resolution, if you need help paste your xorg.conf here. for your wireless, can you do ```
lspci
``` in terminal and then paste the output here; that way we can figure out exactly what card is in your laptop.

---

### Post by bwhite82 on 2007-04-19
> **papafred07 said:**
> After reading about Ubuntu for several months, I decided to take a chance and install it (I waited until today for the release of 7.04).  While I've managed to install it properly, I am encountering a couple problems.  First of all, my resolution is capped much lower than my screens res of 1440x900 (I am running on a Dell e1405 laptop).  Furthermore, I have had no success in establishing any sort of connection with my wireless network.  I had no luck connecting to either a friends unsecured network, or my secured one. any suggestions?  On another note, does anyone know if it is possible to sync my Microsoft Zune with Ubuntu?

thanks for the help!

Fred

Welcome to Linux! Although you've happened upon the best new-user friendly distro in the biz, there is always going to be some configuring to do with a new installation. The wiki, [http://wiki.ubuntu.com](http://wiki.ubuntu.com) will be your best friend for quite a while for a new install. My guess is that you have an ATI x1300/1400? And perhaps a broadcom wireless adaptor? It is absolutely crucial to find out what hardware is in your machine to configure it properly.

---

### Post by papafred07 on 2007-04-20
hey guys,

thanks for the help!

whenever i entered the xorg.conf to terminal.. this is what i got:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Inte$
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection



and for the wireless, i got this..

fred@MissLopez:~$ lspci
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by papafred07 on 2007-04-21
the resolution seems to be right, but whenever I try to adjust it in the menu.. there isn't an option for 1440x900

---

### Post by lagartoflojo on 2007-04-21
Papafred,
I have an Intel card also (00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)) and the way of getting the right resolution is **installing the 915resolution package**, available through Synaptic. I had to do nothing but install the package and restart the computer to get my desired resolution (1680x1050).

The program's website states that it works on the 945 also:
*[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)*
> 915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets. This includes the 830, 845G, 855G, and 865G chipsets, as well as 915G, 915GM, 945G, 946GZ, G965, and Q965 chipsets. This modification is neccessary to allow the display of certain graphics resolutions for an Xorg or XFree86 graphics server.

The website also points to the following blog post, which might apply to you:
auto915Resolution - Ubuntu Resolution fix for Intel chipset 8x-945
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

Now, as I said before, maybe the only thing you have to do is install the package and restart. Try that first (as it worked for me) and if it doesn't help, check the websites I have pointed out to you.

One more thing: 915resolution's description sounds a little scary, but it won't harm your computer:
> 915resolution's modifications of the BIOS are transient. There is no risk of permanent modification of the BIOS.

---

### Post by fakie_flip on 2007-05-08
Microsoft likes to be proprietary crap. Sell the Zune on Ebay and buy something Linux compatible that isn't made by MS.

---

