---
title: "Problem at installation of Ubunt Studio 7.10"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Archi82 on 2007-11-25
Hi, i'm a new member in the community of Ubuntu. I downloaded the image of Ubuntu Studio 7.10 (alternate-amd64 version) from UbuntuStudio.org, to install ubuntustudio on my pc, but i encountered some problems:
1) The image of the distribution is not a DVD image but a CD image. So the problem arises about burning an image witn 812 MB on a CD. But anyway i managed, overtaking some difficulties, to burn it correctly.
2) When booting the system with this cd appears the display of installation but the installing options are the following: Install in text mode, OEM for manifacturers, Check disk integrity, Test memory, Boot from first disk, etc. So i can install the distribution only in text mode. infact, after installation, UbuntuStudio is not in graphics mode but i see only a command line. How can i resolve this problem? Is the image i downloaded from your site wrong or corrupt? (i checked its integrity with md5sum) How can i start ubuntu in graphics mode?
Thanks a lot.
Bye

Archi82

---

### Post by philinux on 2007-11-25
Not installed this way before but try gdm at the command prompt.

---

### Post by blitz_whiz on 2007-12-22
Hola!

I have been having the same trouble. I have installed ubuntustudio on two laptops but I had to installl gutsy first and then install packages. I would just like to boot and install from the DVD. I have dualboot with Vista. And the install of Studio happens only in text mode and I can't even start GDM. I am kinda dumb at it and trying to get better. Can someone tell me how to start this in Graphical mode or even better install Ubuntu studio in graphical mode. when istalling from DVD there is no install ubuntu option. theres just a install in text mode and OEM option. Guide please.

---

### Post by AndyFitz on 2007-12-22
Hello, I had this problem. I found out that when I installed Ubuntu Studio, I didn't install the Ubuntu Desktop. When the screen comes up during the text installation asking what software you want to install (2D/3D, sound, video, etc) there is an option to install the Desktop. Enable that and you're golden. I hope this solves your problem. (There may be another way to solve this from the command line, but I just did a reinstall since I hadn't put any valuable data on Ubuntu yet)

---

