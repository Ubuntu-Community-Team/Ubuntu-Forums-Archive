---
title: "how do i install AIGLX?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by 005david on 2007-09-23
people keep posting some wiki about it, but the links are broken.  no links, just tell me what i need to do.  if i need to know what gpu i have, i am going to need a way to find out.


w/o AIGLX, is it even possible to run beryl? (i tried, but it reboots my computer when i switch to beryl as my window manager)

there is a reason i'm called a beginner :P

---

### Post by st33med on 2007-09-23
First off, please post questions about compositing in the Desktop Effects forum.
Second, it is merged into Xorg already. So I wouldn't worry about it. 
Third, AIGLX is used for indirect rendering. It is only needed if you are using an ATI/Intel Graphics card. To find out your Graphics card:
```
lspci | grep display
```
In the terminal.

---

### Post by 005david on 2007-09-23
lspci | grep display doesn't do anything, and just lspci gives me this:

david@mark-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
david@mark-desktop:~$ 



i don't know if i can see it in there or not...

---

### Post by st33med on 2007-09-23
> **005david said:**
> lspci | grep display doesn't do anything, and just lspci gives me this:

david@mark-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
david@mark-desktop:~$ 



i don't know if i can see it in there or not...
It is the last one. This is a 64MB card that I have never heard of. Might run compiz.
And, sorry, it should have been lspci | grep VGA.

---

### Post by 005david on 2007-09-23
> **st33med said:**
> It is the last one. This is a 64MB card that I have never heard of. Might run compiz.
And, sorry, it should have been lspci | grep VGA.

currently i have my window manager set to compiz, but is there anything special about that?  anything beryl-like?

---

### Post by st33med on 2007-09-23
You mean you are using Desktop Effects? Or are you using Compiz Fusion?

Compiz has a few features of Beryl (not all). If you want to configure Compiz, download this:
```
sudo apt-get install gnome-compiz-manager
```

---

