---
title: "wireless latitude D505"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by crawall on 2008-01-23
I'm completely new to Linux so please bear with me. I have a Dell Latitude D505. I also don't have the original Windows XP install disk (the computer wasn't used for about 2 years but after hearing all the good stuff of Ubuntu I took it out of the cupboard).

I installed Ubuntu 7.10 but I can't connect to wireless.

So here are my questions:

1) How do I find out what kind of wireless card I have?

2) When I start Ubuntu I can go to System->Administration->Network and it's set on 'enable roaming mode'...is this the right setting or do i have to change this? Something is clearly wrong because it doesn't connect.

3) what is the ndiswrapper thing?

thanks for any reply
Crawall

---

### Post by wormser on 2008-01-23
1.  To find your card run the following command and post the results.  Applications> Accessories> Terminal.

```
lspci
```

2.  Yes, you want to enable roaming mode.  Are you using WEP or WPA?  It could have something to do with them.  We will be able to help more when we have your card details.  

3.  Ndiswrapper is a way to get your hardware working.  I use Restricted Drivers to get mine working.  It is easier but will depend on what type of card you have.  System> Administration> Restricted Drivers Manager.

---

### Post by crawall on 2008-01-24
the lspci - report

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

The roaming is enabled

What should i do next?

---

### Post by wormser on 2008-01-24
> **crawall said:**
> 
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

What should i do next?

In the quote is your wifi card.

With hardware problems it is always best to advance search the forum with the title only option of the model number.

I found one post marked resolved [here]("http://ubuntuforums.org/showthread.php?t=4327&highlight=2100+intel").  It looks like it will solve your issue but I am not sure.  It is worth a shot.

> Look at /boot/grub/menu.lst
Find a line like:
# kopt=root=/dev/hda3 ro

Add acpi=noirq to the end, i.e.
# kopt=root=/dev/hda3 ro acpi=noirq

I installed with the acpi=noirq option on my Dell (D600) with no
problem and used the wireless to finidh my install.

Since your a noob I will translate it for you.  Applications> Accessories> Terminal.

```
gksudo gedit /boot/grub/menu.lst
```

Towards the bottom of the file you will see the line that boot Ubuntu.  You need to add **acpi=noirq** to the end of it.  Save the file then reboot.  Test it.  If that does not work then you can go back and delete the line.

---

### Post by crawall on 2008-01-30
no change

---

### Post by crawall on 2008-01-30
i'm willing to try any other idea to get it working

---

### Post by bzzzzz on 2008-03-20
In order to give you a bit of confidence I thought I'd let you know that I'm using a dell d505 and the wireless connection is working. 

I am however using 7.04 because I have installed edubuntu using wubi.

Have you found the network that you wish to connect to from system => network and then in the connection menu double click wireless connection

---

