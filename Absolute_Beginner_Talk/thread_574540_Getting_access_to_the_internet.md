---
title: "Getting access to the internet"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Smatt454 on 2007-10-12
I just installed an older network card into my computer running ubuntu (the computer is a Gateway 2000)

When I plug the Ethernet chord into the computer, I get a "PC/activity" light on the modem. However, my internet access wont work on Ubuntu. Any Ideas?:guitar:

---

### Post by defrex on 2007-10-12
Type *ifconfig* into a command line and post the results.

---

### Post by blues-geek on 2007-10-12
For starters check to see if your computer is getting an IP address. Type 'ifconfig' in a terminal window. You should get some numbers listed beside 'inet addr:'

---

### Post by Smatt454 on 2007-10-12
results of ifconfig 

 ```
 lo                             Link encap:Local Loopback
                                              inet addr:127.0.0.1  Mask:255.0.0.0
                                              inet6 aar:  ::1/128   Scope: Host
                                             UP LOOPBACK RUNNING  MTU:16346     Metric:1
                                             RX packets:2 errors:0  dropped:0  overruns: 0  frame:0
                                             TX packets:2 errors:0  dropped:0  overruns: 0  carrier:0
                                             collisions:0  txqueuelen:0
                                             RX bytes:100 (100.0  b)   TX bytes:100  (100.0 b)  
```

---

### Post by blues-geek on 2007-10-13
It looks like your network card didn't install properly as there is no eth0 interface in the ifconfig output. Try typing ```
lspci
``` at the command line and post the results.

---

### Post by Smatt454 on 2007-10-13
results of slpci

```

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX - Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation  440LX/EX -  82443LX/EX - AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Multimedia  audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:00.0 VGA compatable controller: Chromatic Research Inc. Mpact 2 (rev 41)

```

---

### Post by blues-geek on 2007-10-13
Your network card is definitely not loading. You will have to try to find some drivers for the card or try another model. I would start by checking an Ubuntu Hardware Compatibility List like the one at [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) . See if your card is listed there and what they say about it. Sorry I couldn't help more.

---

### Post by Smatt454 on 2007-10-13
It's fine....I didn't think the card would work anyway....it's ancient.

Thanks for trying:guitar:

---

### Post by Happy_Man on 2007-10-13
There's always ndiswrapper. You can try that... to get it, boot up the LiveCD, use the Synaptic Package Manager *on the CD Live session* to install it, and then install the OS again (sorry). Hopefully, the ndiswrapper package got installed along with the rest of the OS. Now go find your Windows driver CD that has the driver for the card on it, and use ndiswrapper to install it, and then reboot. Hopefully your card will work now.

---

