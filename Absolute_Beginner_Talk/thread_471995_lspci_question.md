---
title: "lspci question"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-12
Should lspci not see a soundblaster audigy card which has been physically installed? Or do I need to find drivers (for feisty)  for it first?

Current lspci output only shows the other onboard audio stuff. No sign of the soundblaster. Output is:


richard@kids:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
richard@kids:~$ lspci -t
-[0000:00]-+-00.0
           +-01.0-[0000:01]----00.0
           +-0a.0
           +-10.0
           +-10.1
           +-10.2
           +-10.3
           +-11.0
           +-11.1
           +-11.5
           \-12.0

---

### Post by grahams on 2007-06-13
I believe lspci will list any device that replies with an PCI system ID regardless of the a driver being loaded.

Do you know if the sound card works with another OS or another system?

---

### Post by ginestre on 2007-06-13
> **grahams said:**
> 

Do you know if the sound card works with another OS or another system?

It worked on the same PC under winXP before I changed operating systems a month ago...

---

### Post by zvacet on 2007-06-13
```
lshw
```

---

### Post by ginestre on 2007-06-13
> **zvacet said:**
> ```
lshw
```

That doesn't list it either. Is this likely to be a <gasp> hardware problem  </gasp> ? If so, is there some way to check its physical functionality, a bit like Mr Gates' helpful  "This ..... is/is not functioning properly" message?

---

### Post by grahams on 2007-06-13
It may be faster to check to see if a Window system can still access the card. If it can not you've confirmed you have a H/W problem.

If the card does work on Windows and still can't be seen in Linux it may be hidden by a PCI bridge that the kernel  (or BIOS) can't see behind. You could try moving it to an I/O slot that has a card installed and that is seen by lspci.

---

