---
title: "wifi problems on hp pavilion dv6000"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-13
hey guys, I just finished installing ubuntu on my laptop but the wifi dosent work. i checked in sys/add/networking and all i have is eth0. 

i ran lspci and I get..

mike@mike-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0 3)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Gra phics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics C ontroller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio  Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Por t 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Por t 2 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1  (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2  (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3  (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4  (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI C ontroller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Brid ge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controll er (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Stor age Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (re v 02)
0000:02:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev  01)
0000:05:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 0 2)
mike@mike-laptop:~$


dose anyone know what i should do? i need wifi on this laptop.

---

### Post by Skia_42 on 2007-03-13
What version of Ubuntu do you have? My laptop has an intel wireless card that did not work automatically in 6.06. I got it working but I do not know how. Wireless worked automatically in 6.10. It's probably worth giving a try.

---

### Post by siciliancasanova on 2007-03-13
First of all, what kind of card is it and have you tried to install a driver for it yet?

Second, what is your output for ```
iwconfig
```?

EDIT:  Your system is seeing that there is something there on this line: ```
0000:02:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
```

---

### Post by da1nonlymikeo on 2007-03-14
mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


im on ubuntu 6.06
im not sure what kind of card it is and i havent tryed to install drivers because i wouldent know wich ones to try to install?

---

### Post by siciliancasanova on 2007-03-14
What is the exact model number in the 6000 series?

---

### Post by charles.g.moore on 2007-03-14
Find out what kinda card you have.

I am running 6.06 on a dv6000t

My intel card worked out of the box but if you run the broadcom card use something in these forums

This forum is great for other stuff on your laptop too...
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)

Broadcom cards
[http://www.ubuntuforums.org/showthread.php?t=145558](http://www.ubuntuforums.org/showthread.php?t=145558)

Make sure to use the nm-applet after you get the card drivers working, it makes grabbing a wireless network simple 

Also wpa_supplicant allowed me to use encryption

I did a forum search for dv6000 and it kicked back some good stuff

Good luck

---

