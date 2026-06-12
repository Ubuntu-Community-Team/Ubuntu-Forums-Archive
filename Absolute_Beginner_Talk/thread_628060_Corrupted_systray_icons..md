---
title: "Corrupted systray icons."
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by joku_muko on 2007-11-30
Hello, been using Gutsy Gibbon for the last week or so. Everything good so far. But there is this little annoyance of corrupted systray icons. I'm pretty sure its not app specific happened with amarok too. (Current pic is of Quod Libet). I was not able to find any other threads on this, just mainly overlapping desktop icons and some such.

Image:

[IMG]http://img516.imageshack.us/img516/299/deskcorruptvi3.png[/IMG]

---

### Post by jcsteele on 2007-11-30
has it always done this?  or did it recently start.

Does it occur if you login with a different user? (To add a new user goto System -> Administration -> Users and Groups)

//jcs

---

### Post by joku_muko on 2007-11-30
Its happened off and on since I can remember. It will come and go. Currently it is not there and I havent done anything but post to this forum. I will try another user.

Edit: I should also mention that it happened my first install (this is my 2nd...) screwed some things up with sudo and didnt know I could undo them so I just reformatted.

---

### Post by jcsteele on 2007-11-30
It might be an issue with your video card....not sure yet.

What kind of card do you have?  using open source or proprietary drivers?  can you post output of "lspci" ?

//jcs

---

### Post by joku_muko on 2007-11-30
Yes using the restricted drivers.

$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0c.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

---

### Post by jcsteele on 2007-11-30
what happens if you revert back to non-restricted drivers?  Do you still have functionality (i.e. is it usable?)

I dont have an Nvidia card, so I might not be much help....however over at ubuntuguide.org they have some information....you might already have this done though.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

//jcs

---

