---
title: "Nforce 410 sound issues. (Biostar Tforce)"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Exile29 on 2006-04-10
I am running a Biostar Tforce 6100 - 939.
I was able to install i386 Badger yesterday (I was going to install AMD64 version, but I was worried about it being so new, and me being such a noob).

Anyhow, I like it so far, but I REALLY wish I could get the sound to work. 
I went to the Nvidia website and downloaded [http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)
Opened Terminal and typed: sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run

At first I was prompted to install an app (who's name I don't recall) like bintools or something. Then I tried sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run and got into the install dialouge. It propmted me to install NIC and Sound drivers. I don't use the onboard NIC, so I just selected sound. As it was installing, I got an error message and it crapped out. I am at work, so I con't have a transcript of the error. Sorry. I will post it tonight when I get home.

---

### Post by Exile29 on 2006-04-10
Here is the installer log.
From what it says,  I guess I need the source for 2.6.16-10-386 installed. Why does it need the source anyhow? 
In any case, I am going to look for it in Synaptic. Would that be the correct spot to download and install the source? Here goes nothing! (It's a good thing Ubuntu is so easy to install!)

Pasted from log--------------------------------------------

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Mon Apr 10 21:48:15 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.12-10-386 (buildd@terranova) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11
   16:13:17 UTC 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.

---

### Post by Exile29 on 2006-04-11
Okay. So I loaded the kernel source for 2.6.12-10 and ran the installer again, making sure that I pointed to the source location. 
Compiler error...
So then I loaded the compiler version referenced in the error.
Compiler error...
Reboot. Rerun installer.
Compiler error...

Well, I decided to search around a bit more and see if there is another way to do this.

Installed the GLX drivers.
Edited xorg.conf
Nothing. 
Actually, that isn't true. When I reboot, I get a message saying that xserver won't start.  ](*,) 

Okay. I plan to reinstall Ubuntu tonight. I am determined to give linux a fair chance.

Does ANYBODY have ANY suggestions that might make my next install a lot smoother? All I am really looking for is sound. I can cope with the default drivers that load for my board.

---

### Post by Burgresso on 2006-07-24
Hey - I have the exact same MOBO and sound works great, out of the box! Maybe it something else, like something is not hooked up right or something?

I'm a noob myself, and build my CP from scratch, and the sound worked great with the defaults.

---

