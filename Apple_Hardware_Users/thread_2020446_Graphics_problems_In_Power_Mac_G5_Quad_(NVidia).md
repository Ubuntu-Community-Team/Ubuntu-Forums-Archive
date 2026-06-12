---
title: "Graphics problems In Power Mac G5 Quad (NVidia)"
date: 2012-07-08
forum: Apple Hardware Users
---

### Post by krespim on 2012-07-08
Hi all,
I've installed Ubuntu 12.04 on an old PPC and is running but things are not good yet. 

Basically the graphical resolution is under par and specially the icons, on the left bar, are a white box. This seems to be an issue with the graphics card and there are several workarounds out there. Unfortunately I seem to so far have tried the wrong ones since none as worked. So these are the specification of the computer:

```
Model Name:	**Power Mac G5 Quad**
  Model Identifier:	PowerMac11,2
  Processor Name:	PowerPC G5 (1.1)
  Processor Speed:	2.5 GHz
  Number Of CPUs:	4
  L2 Cache (per CPU):	1 MB
  Memory:	2.5 GB
  Bus Speed:	1.25 GHz
  Boot ROM Version:	5.2.7f1

**NVIDIA GeForce 660**0:

  Chipset Model:	G**eForce 6600**
  Type:	Display
  Bus:	PCIe
  Slot:	SLOT-1
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0141
  Revision ID:	0x00a4
  ROM Revision:	2149
  Displays:
**LG W2261**:
  Resolution:	1920 x 1080 @ 60 Hz
  Depth:	32-bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display Connector:
  Status:	No display connected
```

Does anyone have a good solution to sort out the graphics card problem for this model?

A bonus point for a good driver to speed up the internet connection using a ASUS USB-N13 adaptor.

---

### Post by snip3r8 on 2012-07-08
First off , do you have the driver for the nvidia card installed?

---

### Post by krespim on 2012-07-08
> **snip3r8 said:**
> First off , do you have the driver for the nvidia card installed?

I don't think so. When I go to System settings -> Details the driver shows as "unknow". Also I did not try to install it.

---

### Post by snip3r8 on 2012-07-08
If you search in the launcher for the word driver , something should pop up for installing proprietary drivers, I would tell you the exact name but I'm sitting through an install an all my other boxes run osx.i will post as soon as I'm done though.it should automatically pick up the driver you need and it will download and install it for you.

---

### Post by snip3r8 on 2012-07-08
Ok the application you are looking for is called additional drivers, hope this helps.

---

### Post by krespim on 2012-07-08
> **snip3r8 said:**
> If you search in the launcher for the word driver , something should pop up for installing proprietary drivers, I would tell you the exact name but I'm sitting through an install an all my other boxes run osx.i will post as soon as I'm done though.it should automatically pick up the driver you need and it will download and install it for you.


Thanks! 

I've just now searched for drivers and something like "additional drivers" comes up". However, and this an issue that I've noticed earlier, it crashes everytime I try to start it (application jockey-gtk). I'll to take a blind shot and nstall jockey-kde to see if that works better.

---

### Post by snip3r8 on 2012-07-08
It just might , mine had some trouble starting up too , you could also try searching in the software centre for a package named NVidia binary X.Org driver .

---

### Post by krespim on 2012-07-08
> **snip3r8 said:**
> It just might , mine had some trouble starting up too , you could also try searching in the software centre for a package named NVidia binary X.Org driver .

The jockey package does not work and I cannot install the  NVidia binary X.Org driver from the software center. It show up on the list but tells me that the source is not available to me:

"There isn’t a software package called “nvidia-current” in your current software sources."

---

### Post by rsavage on 2012-07-08
As the PowerPC FAQ states, there are no proprietary video drivers available for PowerPC.

---

### Post by snip3r8 on 2012-07-08
> **rsavage said:**
> As the PowerPC FAQ states, there are no proprietary video drivers available for PowerPC.
Nouveau maybe ? [http://en.wikipedia.org/wiki/Nouveau_(software)]("http://en.wikipedia.org/wiki/Nouveau_(software)") it should be installed by default although maybe checking if xserver-xorg-video-nouveau is installed would be worth a shot.

You may also want to read the opinions voiced here [http://forums.macrumors.com/archive/index.php/t-1247393.html]("http://forums.macrumors.com/archive/index.php/t-1247393.html")

---

### Post by krespim on 2012-07-08
> **rsavage said:**
> As the PowerPC FAQ states, there are no proprietary video drivers available for PowerPC.

Fair enough, but in this case the additional drivers module is not working at all. I don't want this to be interpreted the wrong way - I highly value your and others work towards making Ubuntu PPC a reality - I am just looking for a working solution.

---

### Post by rsavage on 2012-07-08
> **snip3r8 said:**
> 
You may also want to read the opinions voiced here [http://forums.macrumors.com/archive/index.php/t-1247393.html](http://forums.macrumors.com/archive/index.php/t-1247393.html)

I don't know what that is meant to teach us, apart from there are a lot of ignorant and negative people in the world.  

To get back to the OP, the problem is mentioned on the PowerPC known issues page, with a workaround to drop down to unity 2d.  Since I cannot run unity-3d nor do i have nouveau I'm afraid I cannot help any further than that.  If you want fancy compiz stuff then you can add that to unity-2d which will give you pretty much the same as unity-3d.

---

### Post by snip3r8 on 2012-07-08
> **rsavage said:**
> I don't know what that is meant to teach us, apart from there are a lot of ignorant and negative people in the world.  


Oh no , thats this link [https://plus.google.com/]("https://plus.google.com/"):popcorn:

Jokes aside though im pretty sure nouveau will help on top of switching to 2d, I heard Torvalds used to run a G5 ,thats probably why he was so , um... ,vocal about Nvidia

---

### Post by BenTin2 on 2013-04-07
Sorry to pick up this thread again. But. **Any luck out there!?** I've just been struggling with the nv driver(less) issue for about a week now, and am also plagued by the white unity gui buttons... and jockey still won't even load, just dumps - but i suspect that one is a non-issue, since the proprietary driver is nothing more than a dream. 

[ G5(ppc) late-2005 model, with nv geforce 6600 ]

---

### Post by venividivici24 on 2013-06-02
I'm sorry for another bump, but anyway, I would recommend that you try Lubuntu 12.04 LTS or 13.04 because they don't have Unity, so you won't have the white icon problem, plus Lubuntu is faster than Ubuntu. If you get a kernel panic on Lubuntu 13.04, your best bet would be 12.04 because 12.10 has the same kernel issue.

Good luck.

---

