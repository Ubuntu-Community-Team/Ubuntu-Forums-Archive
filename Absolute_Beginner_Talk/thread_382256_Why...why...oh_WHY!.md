---
title: "Why...why...oh WHY!"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by qwazert on 2007-03-11
Why is it that every time I install an "update" it screws up my system?

Once again another "critical" update, and once again my resolution has defaulted back to 800 X 600....

WHY?

What was the command again?  reconfigure -dpkg xserver????

---

### Post by Ek0nomik on 2007-03-11
You could simply run a search in the Ubuntu Forums...

---

### Post by igknighted on 2007-03-11
sudo dpkg-reconfigure xserver-xorg

---

### Post by qwazert on 2007-03-12
OK, that fixed it somewhat. But WHY does this keep happening? Should I ignore updates? They seem to do more harm than good!

---

### Post by freebird54 on 2007-03-12
You don't say what video card you are running, and what drivers.  I've not run into this problem myself - so I guess you're not running ATI with fglrx?  If you are, then maybe I have a fix... 

We love to fix things in these forums, but first we have to know what's happening  :)

---

### Post by qwazert on 2007-03-12
I am using an ATI RagePro. 
IIRC, the last time I tried fglrx it crashed the whole thing!

---

### Post by marx2k on 2007-03-12
back up your /etc/X11/xorg.conf file before each update, obviously...

the line you want to run to reconfigure is in the beginning comments IN that file.

I'm not sure why you're getting your xorg.conf file overwritten each time - obviously that's NOT normal behavior.

---

### Post by arron on 2007-03-12
Did you install a ATI video driver?  It could be after a kernel update, the video does not work properly.  It happened to me.  I went back a kernel version vs setting up the @#$%$# ati driver again.

---

### Post by igknighted on 2007-03-12
> **arron said:**
> Did you install a ATI video driver?  It could be after a kernel update, the video does not work properly.  It happened to me.  I went back a kernel version vs setting up the @#$%$# ati driver again.

Possble, tho doubtful.  Unlike Nvidia the ATI drivers work after a kernel upgrade, just the 3D doesn't.  They still handle your normal 2D desktop quite well.  That is REALLY odd that your xorg.conf gets overwritten each time.  Does it happen with every upgrade?  Or only upgrades relating to graphical components?

---

### Post by qwazert on 2007-03-13
It doesn't happen at EVERY upgrade...and I tried to make careful observations regarding the details of the upgrade just before things went goofy.
As I recall, there was nothing that seemed SYSTEM CRITICAL, which is even more puzzling than usual! There were upgrades for Automatix, Ekiga, and two other titles that I can't remember. 

Now, even though my resolution has been returned to normal, things are still "weird" during the boot process - tiny fonts and login screen, then normal once I've logged in!

Bizzare!

---

