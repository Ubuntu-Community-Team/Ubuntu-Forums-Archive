---
title: "Installing driver for nVIDIA GeForce 6150"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Dan_472 on 2007-04-05
Hello

Short Question:  Where is 'kernel source tree' located?



Background:

If I try to run a 'high-graphics'  game or demo such as  'Amoeba' I get:

Unhandled exception: No direct rendering (hardware acceleration) available! (Check libGL.so.* symlinks)


On the CD that came with the graphics card, I found the following file:
NFORCE-Linux-x86-1[1].0-0311-pkg1.run

Am I on the right track so far?




In console, I type:
sudo ./NFORCE-Linux-x86-1[1].0-0311-pkg1.run


I get:


No precompiled kernel interface was found to match your kernel; this means
  that the installer will need to compile a new kernel interface.


I press 'OK'

 ERROR: Unable to find the kernel source tree for the currently running
         kernel.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.


I press 'OK'

  ERROR: Installation of the network driver has failed.  Please see the file
         '/var/log/nvidia-nforce-installer.log' for details.  You may find
         suggestions on  fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).






Graphics:  nVIDIA GeForce 6150  (built into motherboard)

Motherboard:    Asus M2NPV-VM MicroATX 

Processor:   AMD Athlon 64 X2 Dual-Core 3800+ 2.0 GHz

Ubuntu 6.06 LTS  (32-bit)



Thank you

---

### Post by M$LOL on 2007-04-05
[Here is the Binary Driver Howto for Nvidia cards]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by Dan_472 on 2007-04-05
Got it workin'    Thanks for the link.

---

### Post by djseto on 2007-04-06
I can't get into my GUI. How can I do this from a command line. I downloaded NVIDIA-Linux-x86_64-1.0-9755-pkg2.run from NVidia, but when I run it, I get the same errors

---

### Post by Dan_472 on 2007-04-08
Hi djseto

I don't know too much about computers, but my suggestion, for what it's worth, is to start a new thread about getting your GUI up.  My feeling is that installing the nVidia driver from the command line would be beyond most users,  certainly beyond me.    Hope it all works out well for you.

Dan

---

### Post by Nythain on 2007-04-08
how i install nvidia drivers from command line

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo ln -sf /bin/bash /bin/sh (if running edgy)
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run (replace with whatever version you are installing)
sudo ln -sf /bin/dash /bin/sh (if running edgy)
sudo modprobe nvidia (not sure if its required but it never hurts)
reboot

---

### Post by ScouseMouse on 2007-05-17
> **M$LOL said:**
> [Here is the Binary Driver Howto for Nvidia cards]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Which driver did you use for the NVIDIA Geforce 6150?  I am also the ASUS motherboard with built in graphics card.
:confused:

---

### Post by rwmcgwier on 2007-09-03
Thanks a million.  Your note allowed the last troubling device in my HP Pavilion 9428nr to function at full resolution and with the proper refresh rate and it was automatic.

---

