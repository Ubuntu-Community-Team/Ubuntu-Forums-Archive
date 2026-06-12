---
title: "Sound doesn't work. Please Help."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by MagicalMoose on 2007-06-19
Please help. Ask and I'll tell you whatever you need. Just please get my sound to work. :(

---

### Post by Crafty Kisses on 2007-06-19
> **MagicalMoose said:**
> Please help. Ask and I'll tell you whatever you need. Just please get my sound to work. :(

Go into terminal and type:
```
lspci
```
Let's see what we got.

---

### Post by j002 on 2007-06-19
Look in 'the excerpt from the Ubuntu book'. 

If it isn't under help, you can find it above in the 'sticky' post READ HERE FIRST under 'Official Documentation' and then 'Ubuntu 6.06'.

---

### Post by MagicalMoose on 2007-06-19
> **Codename said:**
> Go into terminal and type:
```
lspci
```
Let's see what we got.

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:03.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

---

### Post by j002 on 2007-06-19
try :

[https://help.ubuntu.com/6.06/book/bo...lProblems.html](https://help.ubuntu.com/6.06/book/bo...lProblems.html)
__________________

---

### Post by j002 on 2007-06-19
[https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html](https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html)

---

### Post by MagicalMoose on 2007-06-19
> **j002 said:**
> try :

[https://help.ubuntu.com/6.06/book/bo...lProblems.html](https://help.ubuntu.com/6.06/book/bo...lProblems.html)
__________________



Page not found :(

---

### Post by j002 on 2007-06-19
try the post I did after that (yes, i know it looks identical).

or :

[https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html](https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html)

about halfway down.

---

