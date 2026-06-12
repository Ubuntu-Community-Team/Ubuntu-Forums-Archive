---
title: "X Server and Nvidia drivers - help!"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-02-23
Hi

I am having a nightmare with trying to get nvidia drivers to work with my 6600 card. I used Envy to install the beta version by mistake which worked. I purged this and installed the recommended 8.2 deb package but X Server wouldn't start. If I changed nvidia to nv in the xorg.conf file it worked. I tried downloading the same driver (9746) from nvidia website and installed but now X Server won't start at all even after trying dpkg reconfigure. :( 

I checked the error log but can't see any errors.

Any help appreciated as my ubuntu box is useless and will just have to use reliable windows (?) instead. :( 

TIA

---

### Post by r4ik on 2007-02-23
To my knowledge you can just run Envy again with the correct version.

---

### Post by geezerone on 2007-02-23
Can't get X server to start though to run the package.

---

### Post by r4ik on 2007-02-23
Sorry misread you're post gracefully.
Suppose you set it to "nv" ?

---

### Post by geezerone on 2007-02-23
Tried nv and vesa to no avail and tried copying a backup to xorg.conf but still no difference. I didn't uninstall the previous package installed by Envy when I tried installing the downloaded 9746 driver (same as envy previous) but don't know if this is what caused it. 

Just want to get X server back :( :confused:

---

### Post by r4ik on 2007-02-23
Other option,

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

Might put things back together again and correct errors.

---

### Post by Nythain on 2007-02-23
ok, try this if you have the offical nvidia driver run package saved on your drive

sudo apt-get --purge - remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
ln -sf /bin/bash /bin/sh
sudo sh (nvidia driver filename here)
ln -sf /bin/dash /bin/sh

change the vesa or nv to nvidia driver in /etc/xorg.conf

sudo modprobe nvidia (not sure if you actually HAVE to do that, but it hasnt ever hurt me)

sudo shutdown -r now

thats pretty much my manual install of official nvidia drivers step by step i've used on countless reformats and kernel upgrades now... speaking of wich, you will have to re-install them any time you change your kernel

it should be noted that if you have a /etc/default/linux-restricted-modules-common you should add nv to it to keep your system from reinstalling the non proprietary... also, not sure of this since i dont run wireless on this box, disabling nv in linux restricted modules common might disable wireless support, but i have never had any problems yet

---

### Post by geezerone on 2007-02-23
Thanks for the replies folks.

I booted into safe mode and managed to get X server to run with dpkg in safe mode. I installed the beta nvidia driver (9626?) which works unlike the up to date driver (9746). Suppose I shall stick to 'a' nvidia driver rather than a non-proprietary one but would be nice to know why this doesn't work.

As a point of note, when I exit X server (ctrl + alt + backspace) x server keeps restarting?

---

