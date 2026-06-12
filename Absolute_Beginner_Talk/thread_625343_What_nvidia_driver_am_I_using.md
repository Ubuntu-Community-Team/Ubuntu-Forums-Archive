---
title: "What nvidia driver am I using"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by kpictjl on 2007-11-27
How do I determine what nvidia driver I am using and how do I know if it's the latest and greatest?

Ubuntu 7.10

```
$ lspci | grep idia
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```


Here's a chunk of my /etc/X11/xorg.conf
```
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```

---

### Post by PeterJS on 2007-11-27
> **kpictjl said:**
> 
Here's a chunk of my /etc/X11/xorg.conf
```
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
**    Driver         "nvidia"**
EndSection

```

You are using the Nvidia binary driver, which is the one that works with all the 3d goodness. The open source driver is called "nv".

---

### Post by kpictjl on 2007-11-27
So that's it?  Isn't there version number or a release date or something?

---

### Post by FuturePilot on 2007-11-27
This will tell you
```
cat /proc/driver/nvidia/version
```

If you're using the one in the Gutsy repos it's the 9639 driver.

---

### Post by kpictjl on 2007-11-27
Here's what I get.
```
$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
GCC version:  gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
```

How does that relate then to the nvidia drivers on the nvidia [web site]("http://www.nvidia.com/object/linux_display_archive.html").

On that page I don't see the 9639.
	> Linux Display Driver - x86
Version: 1.0-9746
Operating System: Linux x86
Release Date: December 21, 2006
  
	Linux Display Driver - x86
Version: 1.0-9631
Operating System: Linux x86
Release Date: December 4, 2006


I see lots of newer drivers, I assume I could install the newer drives at my own risk.

---

### Post by FuturePilot on 2007-11-27
Yes you could. But be careful with witch one you choose. There's two Legacy drivers. The old Legacy driver 71xx and the new Legacy driver 96xx. Your card can use the newer Legacy driver, and the latest version for that is the 9643 driver.
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html")

Sometimes installing the driver manually can be a bit difficult. I would suggest using Envy. It will make sure everything goes smoothly
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by kpictjl on 2007-11-27
Thanks for the advice.  I think I'll just stick with what I have for now.  I was mostly afraid that I was still using a driver from when I initially installed Dapper Drake.

---

### Post by FuturePilot on 2007-11-27
No problem:)
Whenever you upgrade to the next version of Ubuntu you get a new driver.

---

