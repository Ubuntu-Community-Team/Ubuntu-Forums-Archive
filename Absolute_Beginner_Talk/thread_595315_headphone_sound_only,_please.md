---
title: "headphone sound only, please"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-10-28
Sounds like (according to my searches) this is a big issue: people, including me, finds that by putting the headphones, the sound plays on their computer AND their headphones.  And as no particular exception to the general population, I would like to have sound coming only through the headphones instead.

Unfortunately, here's where the problem begins: I tried the alsamixer method.  Amazingly, when I mute the front, the head phone mutes as well.  Further, headphone volume cannot be raised.  How can I every get my sound privacy?  Thanks in advance!

---

### Post by Crafty Kisses on 2007-10-28
> **japtar10101 said:**
> Sounds like (according to my searches) this is a big issue: people, including me, finds that by putting the headphones, the sound plays on their computer AND their headphones.  And as no particular exception to the general population, I would like to have sound coming only through the headphones instead.

Unfortunately, here's where the problem begins: I tried the alsamixer method.  Amazingly, when I mute the front, the head phone mutes as well.  Further, headphone volume cannot be raised.  How can I every get my sound privacy?  Thanks in advance!

Post the following output:
```
lspci
```

---

### Post by japtar10101 on 2007-10-28
> **Codename said:**
> Post the following output:
```
lspci
```

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6364
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
02:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:05.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)

```

---

### Post by japtar10101 on 2007-10-28
While I understand the thread maker right next to me is just as desperate, I feel I need this problem solved for the night.  Short story: I'm being selfish, so I'm bumping this thread.  Exactly how does Ubuntu handle audio?

---

