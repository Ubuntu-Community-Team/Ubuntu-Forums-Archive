---
title: "stepmania"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by cesara on 2007-01-16
i'm trying to get stepmania installed and it's going along great.. i run the program by dragging the icon into the terminal but i get this notice that says "Initializing OpenGL...
Your system is reporting that direct rendering is not available.  Please obtain an updated driver from your video card manufacturer."

i've attempted updating my driver through the nvidia site itself but first off i'm n ot sure which driver to download and second of all the drivers are in a .deb format that doesn't want to open no matter what. 

i've also tried doing it the alberto milone way but it doesn't work either can anybody help

---

### Post by hw-tph on 2007-01-16
First off, installing the drivers directly from nvidia's site will mess things up and could cause other problems. There are quick and easy ways to get it going - installing the nvidia-glx package and running **sudo nvidia-glx-config enable**.

[Learn more in the wiki](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).


Håkan

---

### Post by cesara on 2007-01-16
comand not found

---

### Post by Delkster on 2007-01-16
> **cesara said:**
> comand not found

Which command? If you mean the command given by hw-tph (sudo nvidia-glx-config enable), that'll only work after you've installed the driver first. Instructions for that are on the Wiki page to which he gave the link.

---

### Post by cesara on 2007-01-16
alrightt i'm stuck on step 2 
"Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8. Selecting one will also install nvidia-kernel-common. (Note: you have to select the restricted modules first because the nvidia-glx package automatically installs the i386 one - and if you have a generic kernel image, the X will not work.)"

i'm not sure what i should install

---

### Post by cesara on 2007-01-16
nvidia-glx:
 Depends: nvidia-kernel-1.0.9746
  Depends: xserver-xorg-core (>=1:0.99.0-1) but 6.8.2-77.2 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.12.3) but 1.10.1-0ubuntu1 is to be installed

this pops up when i try to install nvidia-glx

---

### Post by Delkster on 2007-01-18
Which driver package did you choose? And which way are you trying to install right now, the wiki way or some other way instructed somewhere else?

If you're doing it as instructed in the wiki, first you need to know which version of the kernel you're running. If you haven't changed it yourself, it's probably -386. If you don't know, enter "uname -a" in the terminal to find out. It's probably either -386 or -generic, assuming that you're running Ubuntu 6.10 (Edgy).

Next, if you're running a 386 version of the kernel, find and install the package linux-386 in Synaptic, if it isn't already installed. If, on the other hand, you found out that you have a -generic version of the kernel, find and install linux-generic. That should get you the linux-restricted-modules package that corresponds to your kernel (that package contains the NVidia driver module for the kernel), and will also make sure that things keep working through future kernel updates.

If those are already installed, the driver module for the kernel should already be working. Next you'll need the nvidia-glx package that'll give you the OpenGL driver and such. Find it in Synaptic and install it. After that you should be able to run "sudo nvidia-glx-config enable". Then reboot the computer, and you should have direct rendering (3D acceleration). Note, though, that if your NVidia card is old enough (GeForce 2 series or older), you'll need to install the nvidia-glx-legacy package instead of nvidia-glx since the latest driver releases from NVidia no longer support the older hardware.


This only applies if you're trying to install the Ubuntu-provided drivers directly from the Ubuntu repositories. Judging by the version numbers shown in your transcript (namely the nvidia-kernel package), I'd guess that you may have been trying to install them from somewhere else according to some other instructions. Either way, you shouldn't mix two installs or instructions. If you need help installing some other driver than the one in the Ubuntu repositories (which is what I gave these instructions for), you'll have to turn to someone else because I know nothing about those.

---

