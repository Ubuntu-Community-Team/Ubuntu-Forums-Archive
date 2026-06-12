---
title: "Changed video cards"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by JBS on 2007-08-08
Hi, I'm somewhat new to Linux.  I'm learning it, but I am very much a beginner.  Besides my main question, I have a couple of others if anybody feels like answering them, but they aren't too important and I'm really interested in getting the first question answered.
Thank you very much for your help.
============================================================
**1)**  I installed Xubuntu onto an older computer.  It had an (ATI) 3D Charger AGP 8MB video card.  It was having some problems so I replaced it with an (NVIDIA) EVGA e-GeForce FX 5500 AGP 256mb video card.  All the experienced readers know where I'm going with this.  I turn my computer on, and get an error that the X Windows system can't start.  It's obvious that the ATI drivers don't work for the NVIDIA card.  How do I fix this?  If it makes a difference, at the moment I am not hooked up to the internet.  In a few days, or maybe even next week, I should be, but in the mean time if I have to install new drivers, I'll have to burn them on a CD.
============================================================
**2) **Stupid question, but I don't think that Xubuntu is mounting my 2 CD ROMS.  How do I check if they're mounted?
============================================================
**3)** When installing Xubuntu I was having problems because I had 1 hard drive and 2 CD ROMS attached.  After Googling the problem I came upon this solution, which worked, but changed my video settings: Disconnect the extra CD ROM, install Xubuntu, then in terminal type sudo gedit /etc/initramfs-tools/modules, then add *piix* to the end of the file, save it, type sudo update-initramfs -u, turn off the computer, re-attach the CD ROM, and reboot.
It worked, but before my screen resolution was 1024x768 (on my ATI card), and after following the instructions the highest resolution I was allowed to go was 800x600.  What happened?

---

### Post by overdrank on 2007-08-08
> **JBS said:**
> Hi, I'm somewhat new to Linux.  I'm learning it, but I am very much a beginner.  Besides my main question, I have a couple of others if anybody feels like answering them, but they aren't too important and I'm really interested in getting the first question answered.
Thank you very much for your help.
============================================================
**1)**  I installed Xubuntu onto an older computer.  It had an (ATI) 3D Charger AGP 8MB video card.  It was having some problems so I replaced it with an (NVIDIA) EVGA e-GeForce FX 5500 AGP 256mb video card.  All the experienced readers know where I'm going with this.  I turn my computer on, and get an error that the X Windows system can't start.  It's obvious that the ATI drivers don't work for the NVIDIA card.  How do I fix this?  If it makes a difference, at the moment I am not hooked up to the internet.  In a few days, or maybe even next week, I should be, but in the mean time if I have to install new drivers, I'll have to burn them on a CD.
============================================================
**2) **Stupid question, but I don't think that Xubuntu is mounting my 2 CD ROMS.  How do I check if they're mounted?
============================================================
**3)** When installing Xubuntu I was having problems because I had 1 hard drive and 2 CD ROMS attached.  After Googling the problem I came upon this solution, which worked, but changed my video settings: Disconnect the extra CD ROM, install Xubuntu, then in terminal type sudo gedit /etc/initramfs-tools/modules, then add *piix* to the end of the file, save it, type sudo update-initramfs -u, turn off the computer, re-attach the CD ROM, and reboot.
It worked, but before my screen resolution was 1024x768 (on my ATI card), and after following the instructions the highest resolution I was allowed to go was 800x600.  What happened?

HI as for your changing of the graphics card 
 When you get the xorg error click ok and then it should bring you to the command prompt, If not use the keys ctrl,alt,F1 all at the same time and this will enter the terminal ( command Pormpt) there you can use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Answer a few question and if you dont know the answer then leave the default answer given. This should bring you back to the desktop after reboot.
As for mounting the drives they should mount when a cd is inserted. If not there is plenty of info around on mounting drives.
The last question I have no idea on that. Good luck! :popcorn:

---

### Post by JBS on 2007-08-08
> **overdrank said:**
> HI as for your changing of the graphics card 
 When you get the xorg error click ok and then it should bring you to the command prompt, If not use the keys ctrl,alt,F1 all at the same time and this will enter the terminal ( command Pormpt) there you can use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Answer a few question and if you dont know the answer then leave the default answer given. This should bring you back to the desktop after reboot.
As for mounting the drives they should mount when a cd is inserted. If not there is plenty of info around on mounting drives.
The last question I have no idea on that. Good luck! :popcorn:
Great, thank you very much for your help, it's exactly what I needed.

---

### Post by dougfractal on 2007-08-08
from /etc/X11/xorg.conf
> # If you have edited this file but would like it to be automatically updated
# again, run the following command:
   sudo dpkg-reconfigure -phigh xserver-xorg

This will give you nv drivers and get you working.

download these
#[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb)

install with 
sudo dpkg -i *.deb

good luck on 2 &3

---

### Post by JBS on 2007-08-08
Thank you, this saves me the trouble of hunting down the drivers myself.
> **dougfractal said:**
> from /etc/X11/xorg.conf


This will give you nv drivers and get you working.

download these
#[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb)

install with 
sudo dpkg -i *.deb

good luck on 2 &3

---

### Post by JBS on 2007-08-09
One last question on the subject.  I have a flash drive that's recognised by Xubuntu so I put the drivers on it.  Now, when I hook the drive up to the other computer, I'm assuming that I need to place the drivers in a specific directory before doing the sudo dpkg -i *.deb right?  Thanks.

> **dougfractal said:**
> from /etc/X11/xorg.conf


This will give you nv drivers and get you working.

download these
#[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb)

install with 
sudo dpkg -i *.deb

good luck on 2 &3

---

### Post by dougfractal on 2007-08-09
> I need to place the drivers in a specific directory before doing the sudo dpkg -i *.deb right? Thanks

cd /todirectory
sudo dpkg -i *.deb

You may have to dpkg in the correct order (you will find out by doing)
I think you want the nvidia-glx-new, if it doesn't work 
sudo apt-get remove nvidia-glx-new

---

