---
title: "can't get external LCD display to work"
date: 2006-12-28
forum: Apple PPC Users
---

### Post by leafw on 2006-12-28
So I have an apple cinema display sitting next to my powerbook Ti 3.5 1Ghz. I have setup the xorg.org according to the ozlabs webpage [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

First I run into screen resolution problems, but I fixed that just by reading the xorg.0.log

Although it works fine when I connect a VGA external monitor, apple cinema displays (digital) result in my laptop having an enlarged, scrolling desktop.

According to the ozlabs how-to website, one has to regset FP_GEN_CNTL. None of both offered options work for my card, the Radeon R250 Lf [FireGL 9000] (rev 01).

Applying xrandr -s 1 as in the xmode script results in the desktop being resized back to laptop-only. Then, when applying xrandr -s 0 and setting the FP_GEN_CNTL,  the desktop no longer scrolls to the right (I use LeftOf), although the mouse can go in there, but the external monitor remains black (with a blinking white led on the bottom right).

I read in the email from benh at the ozlabs webpage that the are other possible higher bits to set, but I am no master of bitwise math when it comes to bash scripts.

I would appreciate any help!

---

### Post by Rippey on 2006-12-28
maybe [this]("http://www.ubuntuforums.org/showthread.php?t=317682") thread wil help you.

---

### Post by leafw on 2006-12-29
Thanks for the pointer, but: where is the aticonfig program? apt-file search can't find it.

The package xserver-xorg-video-ati refers to an ATI binary-only driver, but where is such driver to be found?

The xorg-driver-ati that the poster refers to does not exist in neither the edgy universe nor the multiverse.

---

### Post by Rippey on 2006-12-29
I think it comes with the driver, have you tried executing it from your shell?

---

### Post by leafw on 2006-12-29
It doesn't come with the xserver-xorg-driver-ati (look at the installed files). As I said, apt-file can't find it, which means it does NOT exist for ppc. At least, not in main[-security]/universe/multiverse repositories.

---

### Post by Rippey on 2006-12-29
ow now I see, you have an other driver installed :)
for that howto you'll need to get the fglrx drivers mentioned in the howto.

---

### Post by leafw on 2006-12-30
Well, true! Then: where are these ATI binary-only drivers for linux powerpc?

---

### Post by leafw on 2006-12-30
Which, apparently, are not there at all for ppc:



    * xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.5-11 in amd64 (Release)
    * xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.6-1 in amd64 (Security)
    * xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.5-11 in i386 (Release)
    * xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.6-1 in i386 (Security)

---

### Post by Rippey on 2006-12-31
hmm the only way to do it then is gettong the fglrx source and compile it your self I guess.

---

