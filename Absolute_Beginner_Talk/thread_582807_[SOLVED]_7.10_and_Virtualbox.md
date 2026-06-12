---
title: "[SOLVED] 7.10 and Virtualbox"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-10-20
Has anyone had a problem with trying to install virtualbox on the new 7.10? specifically the fact that when I try and install WinXP and then go into the settings, to make it so I can install it, the usb option is missing. Any thoughts?

---

### Post by Espreon on 2007-10-20
Yeah same here.

---

### Post by erdu on 2007-10-20
Hi there,

Had the same problem. Uninstalling Virtualbox (OSE), installing the closed source version (and rebooting) did the trick for me: all USB devices are working now. Am on Gutsy.

---

### Post by ajeffreys on 2007-10-20
Where do you get the closed source version from?

---

### Post by Chuck58 on 2007-10-20
I had same problem with VB and USB with Ubuntu 7.04, 7.10, all the Linux flavors I have. The open source VirtualBox has problems recognizing USB on this box.

I ditched VB a week ago and will use the free VMware Server and 7.04 and the other flavors of Linux I have on CD's. USB no problem with VMware.

---

### Post by maybeway36 on 2007-10-20
I use VirtualBox over VMWare because I don't need USB :P
The USB and VRDP functionality is not open-source and is only in the propietary product.

---

### Post by slughappy1 on 2007-10-20
Well I went on the virtualbox website and downloaded the one from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads). When I had 7.04 installed and followed the instructions from [http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/) I was able to have usb. But when I try to use the 7.10 version and follow the same how-to, I know that the how-to is for 7.04, there isn't even a usb option. Here is a screen shot, notice the no usb option. Is this a 7.10 version problem, or what?

---

### Post by Borderlander on 2007-10-20
I had the same problem and found this solution in the vbox forums:

me.[http://forums.virtualbox.org/viewtopic.php?t=2302]("http://forums.virtualbox.org/viewtopic.php?t=2302")

it worked for me.

---

### Post by Steve1961 on 2007-10-21
Worked for me as well, although an alternative that also works is to add the following line to /etc/fstab:

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

Just make sure that the devigid entry contains the group id of vboxusers - in my case that's 1002

---

### Post by slughappy1 on 2007-10-21
Thanks, I followed the instructions on the link and it works perfectly now

---

### Post by Jose Catre-Vandis on 2007-10-21
The OSE version does not support USB, so get the "licensed" version from the website

---

