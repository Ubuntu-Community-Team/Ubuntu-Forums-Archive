---
title: "My Linux system so far"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Dazarus on 2006-12-29
Ok so this is my system and what I've done... all be it bad or good...
AMD 64 X2 3800+
2.5 gig DDR ram

raptor 36 gig ( not visible to linux... my windows drive)
230 gig ( 130 data drive for windows and linux)(88 gig for file system)(14 for swap... I know it is to   much but I cant resize it down and recover the space for some reason)

Creative Labs X- Fi card
Nvidia 7900gt 256

my drives come up as the are supposed to except for one thing the file swap drive comes up as floppy one( cant open it says its 80.2gig???). The file system says its 80.2 gig and lists all the system files, is something to worry about?? Other then that the only thing I have to do is get my sound to work with new drivers( theres no sound) and install nvidia drivers

---

### Post by Dazarus on 2006-12-29
I found new vid drivers but I cant get my sound to work

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs Unknown device 0005
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0291 (rev a1)

---

### Post by pseudonym on 2006-12-29
I'm afraid you might be out of luck with the X-Fi card - see what the [ALSA Project]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix"), the main Linux audio developers, have to say.

---

### Post by Dazarus on 2006-12-29
I turned on the ac97 on board sound and I cant even get that to work

---

### Post by pseudonym on 2006-12-30
> **Dazarus said:**
> I turned on the ac97 on board sound and I cant even get that to work
Did you remove your X-Fi before doing that? You can run multiple cards in Linux, but if one of them isn't supported it will likely cause problems in such a setup...

---

