---
title: "Please help installing Nvidia drivers...."
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by madu on 2006-08-10
Hi guys...

I reinstalled Ubuntu yesterday again and now in the process of installing packages and apps.
But I can't seem to install the Nvidia drivers as described in the Ubintu guide. This is what I'm trying to do:

[B]sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop[/B]

after "sudo nvidia-glx-config enable", I get this:
[B] madu@madu-desktop:~$ sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found
 [/B]

This  has worked fine when I had the earlier Ubuntu version.
Can somebody please tell me how to fix this.

Thanks a lot guys...

Madu.

---

### Post by TheRingmaster on 2006-08-10
go to the how-to section in this forum and find automatix in  the stickies. Automatix install nvidia automatically for you.

---

### Post by madu on 2006-08-11
Thanks a lot jpazindustries..
I installed Automatix and installed the Nvidia drivers.. 
Thanks again..

Madu...

---

### Post by TheRingmaster on 2006-08-11
no problem madu

---

