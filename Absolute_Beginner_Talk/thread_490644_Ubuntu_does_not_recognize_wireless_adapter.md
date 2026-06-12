---
title: "Ubuntu does not recognize wireless adapter"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by mattigus on 2007-07-02
I recently bought a new laptop, and have a partitioned drive with Windows on one, Ubuntu on another.  Wireless is not working, and when I do a "netstat -in," all I see is the ethernet and local area network.  What can I do to get my wireless adapter working?

My dad told me I need to rebuild the kernal, but we both don't know how to do that.  What should I do?

---

### Post by mlentink on 2007-07-02
Could you supply some more info? What is the make and model of your wireless card? It copuld also help if you post the output of iwconfig and lspci

---

### Post by mattigus on 2007-07-02
matt@matt-linux:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

matt@matt-linux:~$ lspci
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
matt@matt-linux:~$

---

### Post by mattigus on 2007-07-02
I don't know how to look up wireless make and model.  I can tell you that this is a Dell Inspiron 640m Laptop, however.

---

### Post by mattigus on 2007-07-02
My wireless network adapter is a Broadcom 802.11g Network Adapter.  It definately works, because I'm using it on Windows.

---

### Post by mlentink on 2007-07-02
It's a Broadcom 4311, and Ubuntu is definitely recognizing it, so that's the first step. Now you need to configure it correctly. I saw no ESSID in your iwconfig output. Could you tell us what steps you've taken so far to get it configured?

---

### Post by mattigus on 2007-07-02
I have taken no steps in configuring it.  This is the absolute beginner talk forum, and I am an absolute beginner.  You're going to have to walk me through on the steps.

Thank you, also, for helping me this much.

---

### Post by st33med on 2007-07-02
OOHHHHHHH!!! I have this model. [Follow these instructions.]("http://ubuntuforums.org/showthread.php?t=297092")


EDIT: removed highlights from link, sorry!

---

### Post by mattigus on 2007-07-02
When I did a netstat -in, I see eth0 and eth1.  eth1 is the wired connection that I am using.  eth0, it seems, is the wireless connection.  I'm sorry, but I'm very lost when working with linux.  I hope this helps.

---

### Post by mlentink on 2007-07-02
I would not even attempt to presume I know as much as the collective wisdom iun the abovementioned thread. I suggest you take that as a guide first

---

### Post by st33med on 2007-07-02
did you look at my post?

---

### Post by mattigus on 2007-07-02
Yes I did, St33med.  You're post worked perfectly.

Thank you everyone, who helped me with this.

---

### Post by mlentink on 2007-07-02
Err...
Would you mind marking your thread as 'resolved' so I know I don' t need to come back? If you don't know how: it&#347; in the stickies..

---

