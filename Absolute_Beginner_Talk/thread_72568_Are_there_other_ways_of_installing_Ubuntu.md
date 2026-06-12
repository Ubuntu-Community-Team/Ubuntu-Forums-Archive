---
title: "Are there other ways of installing Ubuntu?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-10-06
I am wondering if there are other ways to install Ubuntu, and I mean other then downloading the .iso, burning it as an image, then rebooting the computer that you want to install it in, and directly installing it to the Hardrive.  I have been trying that with a variety of linux OS's, including Warty, Hoary, DSL, Vector Linux, cAos, and others, but have had no luck.  I either get to an "Enter runlevel" or, in Warty, a "RAMDISK: Compressed image found on block 0", or an error message somewhere, probably because the computer I am trying to install Linux on is old (see Sig, it is a Toshiba Satellite Pro 440CDT, P133Mhz, 32Mb RAM, 1.36Gigs).

So, I am wondering what other options of installing Linux are, other then just making an iso, and installing it that way, since that is obviously not working for me.  I have read something about installing Linux while in Windows (Win98 does work on the machine I want to put Linux on), or through the USB port, are those ways feasible?  Is so, could anybody point me out as to how to install a Linux distro, perferably Ubuntu, through the Windows OS?  USB won't work for Ubuntu since Ubuntu is just a wee bit too big for a USB stick.

Anyway, thanks for reading this, and I hope somebody can help me.

---

### Post by Qrk on 2005-10-06
Debian can install from floppies. 
(but I've never done it, so I can't give you any advice)

---

### Post by DJ_Max on 2005-10-06
There's a Network install, and Floppy. [https://wiki.ubuntu.com/Installation/WithFloppies](https://wiki.ubuntu.com/Installation/WithFloppies)

Also, might I add, I doubt KDE or GNOME will run on your computer.

---

### Post by brentoboy on 2005-10-06
deli linux was made for "win95" generation computers.
You might try that distro.

I think ubuntu (and most other current "friendly" distros) are going to take up a couple of gb and you dont have that much to spare.

---

### Post by Goober on 2005-10-06
Hrm, well, I don't actually have a floppy drive on this machine . . . CDROm yes, and a USB drive, and an Ethernet Port, yes, but no floppy.

I have actually found quite an assortment of what seem to be fairly user-friendly Linux Distros meant for older computers, name Puppy Linux, DSL, VectorLinux and cAos.  From what I have read/seen of them, they are lightweight, and seems to be exactly what I want, but, of course, they don't install.  I shall try deli linux, thanks.

---

### Post by brentoboy on 2005-10-06
I just noticed that you are putting it on a laptop.

Not to discourage you or anything, but linux on laptops hasnt been particularly well worked out until just the last year or so, and I think deli is using an older kernel (smaller, and hits the target devices, so why update)

I wonder if some of the *new* laptop improvments are even in there.

You also might consider installing one of the "light wieght" ubuntu's

search the wiki for a minimal RAM installation.  It will tell you how to install as a server (no gui) and then just add X and a minimal display manager.  that might work out.

---

### Post by SilentCacophony on 2005-10-06
Looks like the small HD is trouble.

Just wondering, have you tried the 'server' install with ubuntu? I think it only uses about 350 MB. See:

[https://wiki.ubuntu.com/Installation/LowMemorySystems]("https://wiki.ubuntu.com/Installation/LowMemorySystems")

There is also a page for installing from windows, though it's aimed at XP. There's a link at the top of the page that may have more info for win9X:

[https://wiki.ubuntu.com/Installation/FromWindows]("https://wiki.ubuntu.com/Installation/FromWindows")

There are more links on the bottom of the LowMemorySystems page, as well.

---

### Post by Goober on 2005-10-06
Hrm, no, I've not even considered the "server" option, since I automatically assumed that would be for a server, y'know, for a company or something.

I shall look at those links later, thanks a lot for suggesting them.

As I keep saying, I will get Linux installed on this Laptop by hook or by crook!  I know others have gotten DSL and such installed on older machines, so I will get Linux working on this one.

---

### Post by DJ_Max on 2005-10-06
[QUOTE=Goober]Hrm, no, I've not even considered the "server" option, since I automatically assumed that would be for a server, y'know, for a company or something.[/QUOTE]
I was going to suggest that, but had to find the link. :eek: 
A 'server' install just install software you would usually install on a webserver, which is essentiall less than a desktop install, and with No GUI. The idea behind that wiki page is that you will only install low resource hungary applications instead of the current applications. For example, instead of KDE, you would use XFCE4, or even smaller, Fluxbox.

---

### Post by Goober on 2005-10-06
Ok, i booted with my 5.10 CD (which works, since I used it to install 5.10 on my Desktop, which I am using right now, hit enter, and everything goes fine until this line: "[     31.003670] input: AT Translated Set 2 keyboard on isa0060/serio0".  Then everything freezes.  For example, I typed this before I went to dinner.  Half an hour later, when I came back, it is at that line, blinking, and not doing anything.

This is the same in the Warty Install CD, except you type "custom" estead of "server", and stops at "RAMDISK: Compressed image found at block 0".  So that doesn't work . . .

---

### Post by welsh_spud on 2005-10-07
Might I suggest you try Puppy Linux. Its a live CD that dumps everything into RAM. I'm pretty sure that you can install it to hard disk.

[http://www.goosee.com/puppy/](http://www.goosee.com/puppy/)

---

