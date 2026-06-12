---
title: "Drivers for ATI"
date: 2010-06-15
forum: Apple Hardware Users
---

### Post by Lukasaurus on 2010-06-15
I have a square, white iMac (22") with an ATI X1600 graphics card. 

I can run games in OSX fine at top settings (WoW, Urban Terror), but when I run some in Ubuntu, it is so slow (especially Urban Terror - which is made for Linux). I can also run games in windows at top settings (TF2 and others). 

So I figured it is probably something to do with graphics drivers. I read a post on here about using the Driver Manager to install ATI graphics drivers, but when I go to the System Options, there is no "Driver Manager" but something like "Hardware Drivers" (I am writing this in OSX, not Ubuntu, so I can't check),  which, when I open, only shows proprietary drivers for wireless networks and not for my graphics card... 

I am running the latest Ubuntu (10). Urban Terror is a pretty low end game, but I also have problem running things like blender and stuff, and have to disable some settings to even get it to run. 

So, how do I install drivers for ATI X1600 and where do I get the drivers? I am pretty noobish at linux. I can work the terminal to some extent, but I am pretty hopeless :)

Thanks
Luke

---

### Post by linuxopjemac on 2010-06-15
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

[http://ubuntuforums.org/showthread.php?t=1109768](http://ubuntuforums.org/showthread.php?t=1109768)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I guess they are in the stock repository of Ubuntu.

---

### Post by Lukasaurus on 2010-06-15
I followed those steps (or tried to), but they are written for an earlier version of Ubuntu, and the only drivers that show up in the hardware drivers manager are some ones for wireless, which I don't need anyway. 

I downloaded the latest catalyst drivers for Linux and it installed the ATI catalyst tool (it now shows up under apps > graphics) but the drivers that it was meant to install didn't install (flgrxinfo says command not installed or something - I know that command is wrong, but I was typing the right one last night), so the catalyst admin setting thing doesn't actually run (says no drivers are installed). 

Help?

Using Ubuntu 10.04

---

### Post by linuxopjemac on 2010-06-16
I think you have two versions now. Can you check in synaptic if you have another one installed? I would purge that one.

---

