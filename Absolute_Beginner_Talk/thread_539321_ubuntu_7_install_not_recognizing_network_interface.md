---
title: "ubuntu 7 install not recognizing network interface"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by doctorc on 2007-08-31
Hi all,
I am new to Ubuntu and decided to install desktop 7  with Windows XP dual boot on my new Dell Vostro 200 machine. Everything  installed fine apart from the Network interface card wasnt recognized. (Intel 82562V)

Any ideas on the easisest way to get this resolved.  

thks

DaveC

---

### Post by southernman on 2007-08-31
Would you post the output of "lspic" and "lsmod"

May need also output of dmesg as well... let's try the two above first though.

Thanks Dave...

---

### Post by anewguy on 2007-08-31
And add "lshw -C network" to that as well if you don't mind.:)

---

### Post by anewguy on 2007-08-31
Try this link, but don't pay any attention to the virtualbox or vm stuff there, just the posts on getting the driver and installing it.  Good luck!:)

---

### Post by southernman on 2007-08-31
> **anewguy said:**
> Try this link, but don't pay any attention to the virtualbox or vm stuff there, just the posts on getting the driver and installing it.  Good luck!:)

Thanks for the backup there anewguy! ;) Where's the link?... curious minds wanna know.

---

### Post by anewguy on 2007-09-01
> **southernman said:**
> Thanks for the backup there anewguy! ;) Where's the link?... curious minds wanna know.

Oh crap!!! That's about 3 times I've done that.  Here's the link again:

[http://ubuntuforums.org/showthread.php?t=502058&highlight=Intel+82562V]("http://ubuntuforums.org/showthread.php?t=502058&highlight=Intel+82562V")

:)

---

### Post by doctorc on 2007-09-04
followed the link and installed the drivers and it now works fine ! thanks  all for your help !

really appreciated.

:)

doctorc

---

### Post by millerdc on 2007-09-07
I have a couple of these Dell Vostro 200's myself. Can someone explain how to make it were I don't have to setup the network driver every time there is a new kernel update?

Also the latest kernel update 2.6.20.16.28.1 causes some weird video anomalies at the bottom of my Dell 20" FP2007 when in 1600x1200 res. It is like it is showing the top of the screen mirrored in a bunch of little rectangles. Is this a video driver issue? The xorg.conf has not changed. Is there an official or better video driver for the integrated intel video card?

---

