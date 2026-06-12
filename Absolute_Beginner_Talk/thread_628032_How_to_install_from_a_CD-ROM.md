---
title: "How to install from a CD-ROM?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by TarB on 2007-11-30
I connected a USB device to my computer. I have the CD that contains the driver for this device. There is no autorun in Linux? My question is as follows: How can I install the needed driver for my device from that CD-ROM? Thank you..

---

### Post by jken146 on 2007-11-30
What sort of USB device is it?  Ubuntu should automatically mount USB storage devices and pop up a file browser window showing the contents.  An icon also appears on the desktop.  If it's a storage device, is it formatted?  In what file system?  Have you successfully used it before (e.g. in Windows)?

```
lsusb
``` will show you which USB devices are detected.

---

### Post by BrendanM on 2007-11-30
I'd also add that unless it's an unusual device, there probably won't be a Linux driver on the CD that came with it. Most hardware manufacturers are way too lazy to write Macintosh or Linux drivers. What kind of hardware are we talking about here anyway?

---

### Post by SaltyCrak on 2007-11-30
just stick the cd in and follow the wizzard. 

i'd advise you to backup your important files... :lolflag:

---

### Post by jken146 on 2007-11-30
@SaltyCrack: Read what the OP wrote!

---

### Post by TarB on 2007-11-30
> **BrendanM said:**
> I'd also add that unless it's an unusual device, there probably won't be a Linux driver on the CD that came with it. Most hardware manufacturers are way too lazy to write Macintosh or Linux drivers. What kind of hardware are we talking about here anyway?

Alfa 500mw Wireless Adapter

---

### Post by TarB on 2007-11-30
> **jken146 said:**
> What sort of USB device is it?  Ubuntu should automatically mount USB storage devices and pop up a file browser window showing the contents.  An icon also appears on the desktop.  If it's a storage device, is it formatted?  In what file system?  Have you successfully used it before (e.g. in Windows)?

```
lsusb
``` will show you which USB devices are detected.

Yes, I can see it there, but how do I actually install the necessary files from the disc that came with it?

---

### Post by TarB on 2007-11-30
> **SaltyCrak said:**
> just stick the cd in and follow the wizzard. 

i'd advise you to backup your important files... :lolflag:

Nothing comes up when I stick the CD in..

---

### Post by jcsteele on 2007-11-30
TarB: your driver CD will not work in ubuntu....your wireless card should be supported under Ubuntu....just plug it in, it does not require any drivers for you to install.  If you cannot get it working, let us know.

//jcs

---

### Post by TarB on 2007-11-30
> **jcsteele said:**
> TarB: your driver CD will not work in ubuntu....your wireless card should be supported under Ubuntu....just plug it in, it does not require any drivers for you to install.  If you cannot get it working, let us know.

//jcs

Well. It seems to be working, but what about the software.. I really need it. In Windows, the light on the card is green when it is working.. in Kubuntu the light is always off... What is going on..?

---

### Post by zabien1970 on 2007-11-30
I have a dell laptop with a green wifi light that always lit with windows, after I switched to ubuntu it didn't light anymore although the wireless still worked, I did see a thread once on how to get the light to work but I never bothered,  if it bothers you search for the workaround, if not just enjoy surfing:)

---

### Post by TarB on 2007-11-30
Well. I don't really care about that light. How do I get the software needed for the card to work in Linux?

---

### Post by jcsteele on 2007-11-30
If your running Ubuntu, you should have an icon near the "clock/date" display in the top menu bar...thats the "network-manager"....try double clicking on it to see if it recognized it.  Can you post the output of a "lsusb"  from your terminal?

//jcs

---

### Post by TarB on 2007-11-30
> **jcsteele said:**
> If your running Ubuntu, you should have an icon near the "clock/date" display in the top menu bar...thats the "network-manager"....try double clicking on it to see if it recognized it.  Can you post the output of a "lsusb"  from your terminal?

//jcs

Bus 004 Device 003: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

It sees it.. How do I install that software?

---

### Post by jcsteele on 2007-11-30
Everything you will ever need is already installed in ubuntu....do not confuse ubuntu with windows where you have to install special software for your printer, network card, etc....ubuntu pretty much (there are special cases however) has everything you will ever need.

As I said, to configure your network, you should have an icon in the upper right hand corner of your screen to configure your network (if your using ubuntu) or the bottom right (if your using kubuntu)....by clicking on the icon it should bring up a menu where you can tell ubuntu to "connect to other wireless network..." and from there you can continue on...check out [https://help.ubuntu.com/7.10/internet/C/troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html) if you have any problems as well.

//jcs

---

### Post by TarB on 2007-12-01
OK. Lets forget about this whole thing. What is the command to install something from a CD-ROM, or install something in general... ? Thank you.

---

### Post by jcsteele on 2007-12-01
click on System -> Administration -> Synaptic Package Manager

//jcs

---

### Post by TarB on 2007-12-01
> **jcsteele said:**
> click on System -> Administration -> Synaptic Package Manager

//jcs

I am running Kubuntu..

---

### Post by jcsteele on 2007-12-01
Sorry, thats my fault.

Look for "Adept Package Manager" under your menu options...I am unfamiliar with the KDE interface, so maybe someone else can give you exact directions to find it if you cannot.

//jcs

---

