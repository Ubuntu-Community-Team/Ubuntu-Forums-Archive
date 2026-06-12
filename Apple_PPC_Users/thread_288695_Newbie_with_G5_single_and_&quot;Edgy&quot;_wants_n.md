---
title: "Newbie with G5 single and &quot;Edgy&quot; wants nVIDIA driver advice."
date: 2006-10-30
forum: Apple PPC Users
---

### Post by RoadTripDK on 2006-10-30
I am a Ubuntu newbie looking for advice about nVIDIA drivers for my G5 single (PowerMac 9.1). The OS X system profiler tells me that I have the following:

> GeForce FX 5200:

  Chipset Model:	GeForce FX 5200
  Type:	Display
  Bus:	AGP
  Slot:	AGP
  VRAM (Total):	64 MB
  Vendor:	nVIDIA (0x10de)
  Device ID:	0x0321
  Revision ID:	0x00b1
  ROM Revision:	2060
  Displays:
SyncMaster:
  Resolution:	1280 x 1024 @ 75 Hz
  Depth:	32-bit Color
  Core Image:	Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported


I have seen some mention about nVIDIA drivers for PPC being extremely poor quality and have also come across the following non-PPC info on installing nVIDIA drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOWTO:_Latest_NVIDIA_drivers]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOWTO:_Latest_NVIDIA_drivers")

Unfortunately, I haven't found anything that definatively advises for or against installing the drivers or explains whether the installation process for PPC is the same. Any advice?

Cheers.

---

### Post by Torrance on 2006-10-30
There are only 3d drivers for the x86 platform, and they're closed-source binaries that Nvidia releases. Unfortunately for every other platform, we're stuck with the fairly low-quality 2d open-source hack known as "nv".... at least until Nouveau gets released (hopefully next year!).

Don't try installing any of those other drivers - you'll screw your system. ;)

---

### Post by RoadTripDK on 2006-10-30
Many thanks.

---

### Post by stream303 on 2006-10-30
I'm happily running the included open-source nv driver on my G5 iMac with Edgy.  Default install results in a 1024x768 screen so the fix was easy:

Ran lspci in terminal to check my card.  Then

```
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
```

Choose nv, then choose native screen resolution (in my case for 20" it was 1680x1050)  Done!

Not the fastest driver around, but it works fine for general purpose needs in the right resolution.  From what I understand, it's our only option at this point.  Looks great to me!

---

