---
title: "Newby needs help"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by buickpwr6 on 2007-06-04
I really do want to use this OS, but it just does not seem to work right for me.

I have tried to download ndiswrapper a 100 times never works and/or does not show up in terminal..
Unable to access the internet. can go to windows and access just fine.

Tried to  get the driver from windows did not work .. I don't know if I did it right or not anyway..
Ubuntu  looks like allot of fun if I ever get to enjoy it..thanks for your time...
My computer is a dell latitude D600..

---

### Post by khardbored on 2007-06-04
Give us some specs please. :)
Output of lspci would be awesomeriffic too.

---

### Post by johnnymac on 2007-06-04
Friend...

I use a D610 so I'm guessing you have the same wireless card - the broadcom card.  I DO NOT use NDISWRAPPER, I use firm-ware cutter and I have never had any issues with wireless access.

do the following from a terminal
```

sudo apt-get install bcm43xx-firmware

reboot the box

```

This should install the firmware you need to get your card running.

---

### Post by buickpwr6 on 2007-06-04
Hey I finally got one thing to work..lol

Here are my specs..

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by buickpwr6 on 2007-06-04
tried this 
sudo apt-get install bcm4306-firmware

reboot the box

reading done
building tree
reading state info..done
 couldn't  find package ???

---

### Post by buickpwr6 on 2007-06-04
HELP???
Any one have any ideas???

---

### Post by Shazaam on 2007-06-04
Did you reboot?

---

### Post by buickpwr6 on 2007-06-04
Will try then what

---

### Post by buickpwr6 on 2007-06-05
Still nothing working???

---

### Post by icechen1 on 2007-06-05
> **johnnymac said:**
> Friend...

I use a D610 so I'm guessing you have the same wireless card - the broadcom card.  I DO NOT use NDISWRAPPER, I use firm-ware cutter and I have never had any issues with wireless access.

do the following from a terminal
```

sudo apt-get install bcm43xx-firmware

reboot the box

```

This should install the firmware you need to get your card running.

I found using the firm-ware extremely slow(max speed 11 mb/s) and in ndiswraper 54 mb/s .But Ndiswrapper is harder to set up.
So use the firm-ware until you are good enough in Linux to set up Ndiswrapper.

---

