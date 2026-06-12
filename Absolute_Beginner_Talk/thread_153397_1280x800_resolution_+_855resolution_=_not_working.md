---
title: "1280x800 resolution + 855resolution = not working"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Xitanto on 2006-03-31
I followed the "Hoary" tutorial regarding 855resolution:

[http://www.ubuntuforums.org/showthread.php?p=880522#post880522](http://www.ubuntuforums.org/showthread.php?p=880522#post880522)

Too bad it didn't work for me using Breezy Badger. When I turn on Ubuntu the login screen is shown in 1280x800 glory. Once I log in the OS reverts to 1024x768. It happens every time (no duh).

Can someone please write up any changes in 5.10 that may have affected 855resolution? If you want any information I'll be able to give it to you, but it may take a sec as I'm still trying to get my Belkin Pre-N wireless card configured with ndiswrapper as well. That isn't working neither.

---

### Post by Mustard on 2006-03-31
Did you download the 855resolution package via Synaptic from the Breezy repositories?

```
Package: 855resolution
Priority: extra
Section: universe/x11
Installed-Size: 108
Maintainer: Kenshi Muto <kmuto@debian.org>
Architecture: i386
Version: 0.4-1ubuntu1
Depends: libc6 (>= 2.3.4-1)
Filename: pool/universe/8/855resolution/855resolution_0.4-1ubuntu1_i386.deb
Size: 10150
MD5sum: 7c6f11f51e4a0bb8a1ce6091911c78f9
Description: resolution modify tool for Intel graphic chipset
 This software changes the resolution of an available vbios mode.
 It will work with Intel 845G/855GM/865G.
 .
 It patches only the RAM version of the video bios, so the new resolution
 is lost each time you reboot. If you want to automatically set the resolution
 on each boot and before X is launched, see /usr/share/doc/855resolution/
 README.Debian for information about configuring the provided initscript.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by Xitanto on 2006-03-31
Yes, I did mustard. I just rechecked, and it's highlighted green. I've installed it from Synaptic. Does it matter that my Intel 915G onboard isn't on that list (845G/855GM/865G)?

---

### Post by Mustard on 2006-03-31
[QUOTE=Xitanto]Yes, I did mustard. I just rechecked, and it's highlighted green. I've installed it from Synaptic. Does it matter that my Intel 915G onboard isn't on that list (845G/855GM/865G)?[/QUOTE]

I couldn't really say for sure.  What I know of this problem I have learnt in the last few minutes. :)

---

### Post by gunderwood on 2006-03-31
855resolution is fine. I've used it with my laptop in breezy with no complications.  

I would suggest you check your xorg.conf file to ensure that the correct resolution is specified. 

Second after running 855resolution to set your resolution run 
855resolution -l 
to ensure that the VBIOS was properly patched.

---

### Post by Xitanto on 2006-03-31
OK - I just figured it out (finally). My X11/xorg.conf had one missing line for the 1280x800 option. I've removed 855resolution and it's all fine now. XD Thanks for the help.

---

