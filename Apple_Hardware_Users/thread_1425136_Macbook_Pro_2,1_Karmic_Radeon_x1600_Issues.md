---
title: "Macbook Pro 2,1 Karmic Radeon x1600 Issues"
date: 2010-03-08
forum: Apple Hardware Users
---

### Post by Mills00013 on 2010-03-08
Hey everyone, just installed karmic on my 2,1 MBP. Everything is running freaking awesome, I couldn't be happier with an operating system.

But I am having issues with my graphics card and getting it to support 3D applications in wine. I have been all around the internet, searched like crazy on this and cant find any solutions newer than 2008, so hopefully someone can come through with something.

The card is working great within the OS itself. All the window animations are maxed with compiz and things are running great. But when I open up vmware player it tells me 3d support is not supported on this machine and when I try to play anything in wine (specifically CSS) it either doesnt open or runs REALLY badly.

So I started researching the x1600 chip and the open source radeon driver. This is what I get for certain commands:

```
$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

```

Then I opened my /etc/X11/xorg.conf file to see what was going on in there (which as I understand it, is supposed to be automatically configured at install by Ubuntu?) and this is the file in its entirety:

```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

So from what I've read, I'm pretty sure that to get correct graphics support, I just need to tweak some settings inside my xorg.conf file, but just to get the ball rolling, I have NO IDEA what I need to even start with on my identifier. My card is a x1600, which according to the man file equates to a RV530/RV560 chip, while the vendor string obviously records it as a R300 chip. So I have no idea where to go from here.

Am I even on the right track to get this going? Whether the chip is a RV5XX or a R3XX chip, either should support 3D acceleration according to the radeon documentation, so the only thing I can propose is that this xorg.conf file is just not correct.

Thanks so much for ANY help!

---

### Post by linuxopjemac on 2010-03-09
From what I read [here]("https://help.ubuntu.com/community/MacBookPro2-1_2-2/Intrepid#Video"), you have the choice of the open source radeon driver, which gives you 3D-support. If you want more, you need to install the closed source **fglrx ATI Proprietary driver**, which is automatically detected in the Hardware Drivers and installs if selected. So I guess if you go to Administration -> Hardware and select that driver it should work. I guess you can also try to find it in the synaptic package manager.

---

### Post by Mills00013 on 2010-03-09
This would normally be true, except, from what I've read, the closed source driver is not supported after kernel 2.6.29 or somewhere therabouts which means jaunty and later (including karmic) doesn't support the closed source driver.

On another note, I've discovered that 3D rendering works great on my card with the open source radeon driver in linux. It just seems to have its issues when I'm running 3D applications in wine. And to be more specific, I haven't tried to run anything that wasn't Counter Strike Source.

Seems at this point it might be the way that wine is addressing my memory card more than the driver being the issue. Although vmware player doesn't recognize my 3D support either, so I'm not entirely sure it doesnt have to do with my xorg.conf file.

Either way, I find it suspicious that X's autoconfig decided that I was running an R300 based chip instead of the RV530. I think that this difference might be why things are not working right, but then again, I have no idea what I'm talking about, so this is all speculation.

---

### Post by Mills00013 on 2010-03-12
Updated my repositories and downloaded a different version of the radeon driver, the radeonhd. After manually configuring my xorg.conf file, the driver was loaded instead but it didn't help the situation at all.

Just thought I'd throw that out in case anyone else is desperate enough to try it, it won't solve anything.

---

### Post by linuxopjemac on 2010-03-12
Radeon Mobility X1600:
You might want to try this:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

---

### Post by Mills00013 on 2010-03-14
The closed source fglrx driver is not supported on kernels 2.6.29 or later, so unless I downgrade my karmic kernel and the other things related to it, it won't run correctly. This seems at this point to be more of a matter of wine maybe just not properly handling these things. I guess I'll just have to wait till lucid is released and see if anything changes in that kernel or with the drivers that comes with it.

---

