---
title: "Need help installing drivers."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by magicsmoke on 2006-10-14
Hello, I'm new to Linux and just installed Ubuntu on a spare HD.  I am trying to install drivers for my hardware (motherboard, video card, sound card,..)

The first device I tried to get drivers for was my video card (Nvidia 7800 gt).  I was following the howto at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) but when I got to typing
[INDENT]sudo nvidia-glx-config enable[/INDENT]
at the terminal, I get an error saying:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

I am not sure what to do from here so if anyone could help, it would be much appreciated.

Other hardware needing drivers:
[INDENT]Asus A8N-SLI DELUX (nForce4) motherboard[/INDENT]
[INDENT]Creative X-fi XtremeMusic sound card[/INDENT]

---

### Post by taurus on 2006-10-14
Try to edit your /etc/X11/xorg.conf by hand and change the Driver from nv to nvidia!!!

```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by magicsmoke on 2006-10-14
ok, I opened it up in gedit, and the only section I saw for the driver name had this:

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

and it looks like "nvidia" is already set and not "nv".

---

### Post by taurus on 2006-10-14
Then log out and X should refresh itself.  You now would see a nVidia logo...  Otherwise, try to reboot and see if you see that nVidia logo before the login screen comes up.

---

### Post by magicsmoke on 2006-10-14
Thank you! I first logged out and back but no logo.  After a reboot, I saw the logo splash screen. :D

---

### Post by taurus on 2006-10-14
> **magicsmoke said:**
> Thank you! I first logged out and back but no logo.  After a reboot, I saw the logo splash screen. :D

Good job.  You are using nvidia for your video card now.  Now, you can run all the 3D stuff that you always wish for...  :)

---

### Post by Delkster on 2006-10-14
> **magicsmoke said:**
> 
Other hardware needing drivers:
[INDENT]Asus A8N-SLI DELUX (nForce4) motherboard[/INDENT]
[INDENT]Creative X-fi XtremeMusic sound card[/INDENT]

Is there something regarding this hardware (for example sound) that doesn't work out of the box? If things seem to work, you probably needn't worry about things like motherboard chipset drivers like you do in Windows.

---

### Post by magicsmoke on 2006-10-14
Actually, my sound card is still not recognized and Creative's website has no available drivers for the X-fi XtremeMusic for linux.  I'm not seeing a howto for this card off the bat either.

---

### Post by taurus on 2006-10-14
What's the output of this command, from a terminal?

```
lspci
```

---

### Post by magicsmoke on 2006-10-14
command not found

---

### Post by magicsmoke on 2006-10-14
sorry, read that as ispci, instead of lspci
output is:

0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0092 (rev a1)
0000:05:06.0 Multimedia audio controller: Creative Labs: Unknown device 0005
0000:05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARai d] Serial ATA Controller (rev 02)
0000:05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link)
0000:05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by Delkster on 2006-10-14
Unfortunately, so far the only clue[1] I've been able to find indicated that there's no support for that card under Linux yet.

[1] [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

---

### Post by taurus on 2006-10-14
So I guess you just have to wait until the second quarter of 2007 or buy a cheap PCI card and use it until then!!!

---

### Post by magicsmoke on 2006-10-14
Yeah....well, thanks for your guys' help.  I'll just enable my onboard audio for now.

---

