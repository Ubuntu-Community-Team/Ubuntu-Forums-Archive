---
title: "Install Problem: The X server(graphical interface) failed to load!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by aubie on 2007-05-12
I downloaded and burned the iso file. When I tried to run Ubuntu from the disc I was given this error message:

Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

I answered "yes".

This came up on the screen:

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revison 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP
Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
                 Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice,
(II) informatonal, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Logfile: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X1/Xorg.conf" 

I went to wiki.x.org. From what I could tell the X server is the latest version. I need help figuring out what is wrong. I am very new to Linux and look forward to replacing Windows on my computer with Ubuntu.

Any help anyone can offer will be greatly appreciated!!!

---

### Post by bobplano on 2007-05-12
there could be a couple reasons for this. one could be the cd was burned with errors, or the .iso is corrupted. so check those first as they are the easiest to fix. post your graphics card here while your at it though

---

### Post by nickoli_02 on 2007-05-12
Most likely, the default video driver that ubuntu uses doesn't like your card. Don't fret, you can get a new and improved driver easy enough. When you boot up into grub, the boot loader, select the recovery mode option. This will give you a command line where you can download and install the correct video driver for your video card. Now for instructions on how to actually do that, check out my signature.

---

### Post by Nebby on 2007-05-14
Hi, I've got the same problem. I've followed everything so far and I'm in recovery mode, but I don't get what I have to do now :confused: 

I've got an nvidia card, so I'm kinda unsure if the stuff in Nickoli's sig'll help me.
Thanks

---

### Post by aubie on 2007-05-14
I also have an NVIDIA graphics card.

---

### Post by RSingh on 2007-05-14
Its obvious that the CD had errors, did you do a cd check before install?

---

### Post by Nebby on 2007-05-14
Yeah, plus its one of the official CDs from Canonical.

---

### Post by RSingh on 2007-05-14
What are your system specs (vid card??? 6x, 7x, 8x) onboard or on AGP?

---

### Post by Nebby on 2007-05-14
7300SE on PCI-E

---

### Post by RSingh on 2007-05-15
Hmmm...not sure why X is crashing.

The problem is that you are trying to run from the live cd and doing a nvidia driver installation would require a reboot and thus you would end up in the same soup again!

I would advise you to do an installation and if the same error occurs then type this in the failsafe terminal that comes after X crash info.

```
 sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig 
```

This should add the properiatory drivers of nvidia and hopefullly fix this problem.

---

### Post by Nebby on 2007-05-15
Aha, well that should work for me straight away since ubuntu is actually installed (I installed it on another computer then moved the harddrive)
Thanks, I'll try it out now:)

EDIT: Okay, I've tried it out now. I tried the[FONT=Courier New] 
[/FONT]```
sudo apt-get install nvidia-glx nvidia-kernel-common
```[FONT=Courier New]
[FONT=Tahoma]line first. That gave me
[/FONT][/FONT]```
Package nvidia-glx is not available, but is referred to by another package. This may mean that the package is missining, has been obsoleted, or is only available from another source.
E: Package nvidia-glx has no installation candidate.
```

```
sudo nvidia-xconfig
```
gave me
```
sudo: nvidia-xconfig: command not found
```

So basically I'm kinda lost now. I'm thinking I should have the restricted bits enabled, maybe? I've tried finding out how to do that on the web but haven't found out how yet.
[FONT=Courier New][FONT=Tahoma][FONT=Courier New]
[/FONT][/FONT][/FONT]

---

### Post by bobplano on 2007-05-15
it sounds like nvidia-glx is in other repos than the ones you have enabled. i don't know what packages are in what repos, but once you enable them it should install then it should work

---

### Post by gandlcarr on 2007-05-15
I had the same issue when i installed it on my Nvidia 7600GT, i was hooked up using the DVI connector,and when i switched it to the VGA Connector i had no Problems. but thats what my issue was.

---

