---
title: "Help with my serial modem, PLEASE!!!"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Eddie Wilson on 2006-12-12
Hello All,
I've posted my problem in other forums and could really find no solution. Where I live I use dialup, I have no other option, and I've been using several different versions of linux for a couple of years. I used Ubuntu 5.10, 6.06,and 6.06.1. I've also used Xandros, and SimplyMepis. I've also played around with DSL and Puppy. Now I'm about to go crazy. I can't get Ubuntu 6.10 to see my modem. Its a standard ActionTec 56k external. Its always worked great but 6.10 acts like its not there. I'm wanting to try 6.10 sooo bad its  driving me crazy. I've tried anything I can think of. Maybe its a serial problem. Please somebody help me.
Thanks All,
Eddie

---

### Post by Kobalt on 2006-12-12
Hello,
Could you please post the result of the following command line : 
```
lspci
```

---

### Post by Eddie Wilson on 2006-12-12
I'm at work right now but I will post it as soon as I get home.
Thanks,
Eddie

---

### Post by Eddie Wilson on 2006-12-13
Here is the result of lspci.

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0e.0 USB Controller: NEC Corporation USB (rev 41)
00:0e.1 USB Controller: NEC Corporation USB (rev 41)
00:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:13.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:13.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Thank you much
Eddie

---

### Post by phidia on 2006-12-13
Try this how to [https://help.ubuntu.com/community/DialupAndFax](https://help.ubuntu.com/community/DialupAndFax)
With Ubuntu and many other debian based systems you need to use the 
'pppconfig' command to set up/create the files needed.

---

### Post by Eddie Wilson on 2006-12-13
Thanks, I'll do that.
Eddie

---

### Post by Eddie Wilson on 2006-12-14
Good Day All,
Well I kept working with Edgy and finally got my modem to work. I could not do it with anything native to Edgy. I tried all the tricks and tips given to me. On my Dapper install I have gnome-ppp. I have a backup of all apt files on another hard drive and I installed gnome-ppp from there. I did an auto detect and IT WORKED! Edgy is in a another partition different than my Dapper install. Now I can play with Edgy without having to worry about breaking anything. Thanks everybody very much for your help. I've said it before and I'll say it again. These forums are the greatest.:-D 
Eddie

---

