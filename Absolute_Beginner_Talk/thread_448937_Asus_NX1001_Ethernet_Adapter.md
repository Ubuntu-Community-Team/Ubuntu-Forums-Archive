---
title: "Asus NX1001 Ethernet Adapter"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-05-19
I have created another computer from various cast-offs. However the motherboard did not have any onboard LAN.
I had done a install of Ubuntu 6.06 when I remembered the LAN card.
I put the card in & re-booted. Ethernet doesn't show in Network Properties, not yet anyway.
The card shows the connection LED OK, but I cannot access the IP address of the router, nor the Internet.
Where do i go from here?
The CD-ROM driver disc does have Linux drivers. I don't know if they are any good since Linux seems to evolve pretty fast. Any advice for me to get this spare Linux box up and running?

---

### Post by overdrank on 2007-05-19
> **Neil Purling said:**
> I have created another computer from various cast-offs. However the motherboard did not have any onboard LAN.
I had done a install of Ubuntu 6.06 when I remembered the LAN card.
I put the card in & re-booted. Ethernet doesn't show in Network Properties, not yet anyway.
The card shows the connection LED OK, but I cannot access the IP address of the router, nor the Internet.
Where do i go from here?
The CD-ROM driver disc does have Linux drivers. I don't know if they are any good since Linux seems to evolve pretty fast. Any advice for me to get this spare Linux box up and running?

Could you post the output from the lspci command?:-k

---

### Post by Neil Purling on 2007-05-20
As requested
code:
neil@neil-spare:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Me mory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Gra phics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Au dio (rev 11)
0000:01:09.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 ( rev 31)
neil@neil-spare:~$

Anything else you want me to do?
As you can see the card doesnt show up in Network Information.

---

### Post by Neil Purling on 2007-05-23
Anyone manged to get one of these LAN cards to work in Ubuntu? The LED's on the LAN card and the router show connection but there is no joy.
Should the LAN card show up in 'Device Manager'?
If you want me to run some more code and post the results I will do so.

---

