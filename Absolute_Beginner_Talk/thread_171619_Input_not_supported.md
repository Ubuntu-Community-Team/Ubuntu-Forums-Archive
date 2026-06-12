---
title: "Input not supported"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by physcsdrk on 2006-05-07
I have an ati radeon 9200.  I have experienced display issues so I followed this howto to update my driver: 

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)


Now I cannot get into Ubuntu.  At the part where it should show the login screen my screen goes black and it says input not supported.  My monitor is an acer 19" widescreen.  When I typed this:
sudo dpkg-reconfigure xserver-xorg
into the terminal it popped up this thing I was supposed to choose the defaults on.  I changed one default from 18" as my screen size to 19-20".  Maybe that is the issue?

Anyways, I am in windows right now (ugh!) cuz I can't get my ubuntu to work.  Any ideas on how to fix it?

---

### Post by Nikusan on 2006-05-08
When you do sudo dpkg-reconfigure xserver-xorg did you choose ati as the driver?

---

### Post by physcsdrk on 2006-05-08
No I chose fgrlx as the driver.  The only other thing I moved from default was the screen size.

---

### Post by Nikusan on 2006-05-08
[QUOTE=physcsdrk]No I chose fgrlx as the driver.  The only other thing I moved from default was the screen size.[/QUOTE]

Well, first thing we need to do I get you up and running with the open source drivers again. So do a dpkg-reconfigure xserver-xorg and choose ati. After that we can try with fglrx again, if you're game. ;-)

---

### Post by physcsdrk on 2006-05-08
I am definately game.  The only problem is that when I go to boot into ubuntu instead of showing the login screen my monitor goes black and this message that says input not supported comes up.

---

### Post by Nikusan on 2006-05-08
[QUOTE=physcsdrk]I am definately game.  The only problem is that when I go to boot into ubuntu instead of showing the login screen my monitor goes black and this message that says input not supported comes up.[/QUOTE]

I have no idea how to fix that, so I guess you'll have to use a live cd to fix the xorg.conf file.
1)Boot into an ubuntu live cd
2)Mount the volume that you installed ubuntu on
3)edit /etc/X11/xorg.conf in a text editor and replace "fglrx" with "ati" in the device section.

You can find more details instructions for those steps around here or maybe some kind soul will go into more detail :)

---

### Post by physcsdrk on 2006-05-08
Thanks.  I didn't even think of using the live cd.  I have been stuck in windows since it happened.

---

### Post by Nikusan on 2006-05-09
[QUOTE=physcsdrk]Thanks.  I didn't even think of using the live cd.  I have been stuck in windows since it happened.[/QUOTE]

I didn't realise you had a windows partition :)
You should also be able to install an ext2 driver and get to the xorg.conf file that way.

---

### Post by physcsdrk on 2006-05-09
Yeah, I have only been using linux for about a week.

---

