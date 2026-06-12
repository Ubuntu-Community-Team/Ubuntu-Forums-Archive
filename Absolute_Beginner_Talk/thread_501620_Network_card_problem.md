---
title: "Network card problem"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Airson on 2007-07-15
I've been toying with Ubuntu for a few days off of the Live CD and finally gave in and did a full install on an old HP earlier today. Everything seems to be in great working order except that it's only detecting my dialup modem and not my ethernet card.

I'm not sure what the card is and I do not know how to check. All I know is that I've got a cable between my router and computer and no network found.

Any help would be greatly appreciated

---

### Post by Happy_Man on 2007-07-15
That's really odd. Generally, Ubuntu should detect most any ethernet card..... what's its model?

---

### Post by oilchangeguy on 2007-07-15
> **Happy_Man said:**
> That's really odd. Generally, Ubuntu should detect most any ethernet card..... what's its model?

the user has stated they don't know what the card is.

---

### Post by Airson on 2007-07-15
> **Happy_Man said:**
> That's really odd. Generally, Ubuntu should detect most any ethernet card..... what's its model?

Is there a way to check without opening the case?

---

### Post by Happy_Man on 2007-07-15
Umm... yeah. On Ubuntu, there should be an option under the System menu called "device manager." Check there to see if the card is listed. If not, then there's a bigger problem at hand.

---

### Post by Airson on 2007-07-15
Ok...I can't seem to find it in the Device Manager, but that could simply because I don't know what I'm looking for.

The card came with the HP Pavilion 700 and has a number 5065 7110 on it. It's not specifically a network card as far as I can tell... it has the printer port, a few sound ports, and a joystick port on it as well. 

I checked the device manager for the number to no avail.

---

### Post by Happy_Man on 2007-07-15
OK, then could you open up a terminal (Applications --> Accessories --> Terminal) and post the output of this command: ```
lspci
```

---

### Post by Airson on 2007-07-15
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)

Edit: I'm getting an eerie feeling that I'm going to be looking for a network card to salvage...but the computer had World of Warcraft installed on it before formatting so it must've had a working ethernet port.

---

### Post by ReaderRat on 2007-07-15
you could try :
```
ifconfig
```
to see if it lists a card.


EDIT:Wrong command 1st time

---

### Post by Airson on 2007-07-15
Command not found. :confused:

Do I run lsconfig straight from the terminal?

edit: edit noted

---

### Post by Airson on 2007-07-15
Results of isconfig:


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6552 (6.3 KiB)  TX bytes:6552 (6.3 KiB)

---

### Post by Airson on 2007-07-16
Anyone?

Sorry for bumping...I'm really interested in Ubuntu and if I can't solve this I will have to pull the plug.

---

