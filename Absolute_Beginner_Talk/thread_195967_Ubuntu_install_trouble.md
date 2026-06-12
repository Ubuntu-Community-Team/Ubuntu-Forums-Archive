---
title: "Ubuntu install trouble"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Aaron Kupniewski on 2006-06-13
When I pop in my Ubuntu desktop cd that I downloaded then click start or install it goes to the desktop.  However, the desktop is just a bunch of random colors.  I've had the same trouble with ubuntu breezy, which is why I stopped using it, and also with debian.  

I also can't even figure out how to install ubuntu on my system from that disc... do I need to do it on the ubuntu GUI or something?

---

### Post by sailor2001 on 2006-06-13
did you reboot into the cd?

---

### Post by Aaron Kupniewski on 2006-06-13
Yah, but if I install Ubuntu by loading it up in windows will that get rid of my desktop problem?  I even tried using the vesa drivers when i did the live cd and it didn't help.

---

### Post by Aaron Kupniewski on 2006-06-15
Again, this happened with Debian also.  I think it has been a couple weeks of googling, IRC Chat, Forums, and I still can't get Linux fullly installed.

Does anyone know what I can do to actually get the GUI working on the ubuntu live disc?

---

### Post by The Cosmic Hobo on 2006-06-15
Have you tried selecting "safe mode graphics" from the boot menu?

---

### Post by nitricacid on 2006-06-15
Go to this site:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

Scroll down the page and download the appropriate 'Alternate install CD'

I had the same problem with the 'Desktop CD' where I couldn't figure out how to install from the CD (it's some kind of a live version)

Let us know how the install goes after you have done the above.

---

### Post by user1397 on 2006-06-15
Here are the steps to install ubnutu via the 6.06 dapper desktop cd:

1) Configure your system BIOS to boot from your cd/dvd rom first.  This can be done by pressing a key (usually F# or Esc) at the first screen when your computer boots.  (You know, the one with your computer's brand name)

2) Download and burn the image file onto a cd (or dvd if the file was intended for dvd's)

3) Insert the cd while you're in windows, and reboot.

4) After Ubuntu loads, double-click on the install icon on the desktop, and just follow the rest of the installer.

---

### Post by Aaron Kupniewski on 2006-06-15
Okay, yeah I get the desktop when I start in the safe mode.  So should I go ahead and install it and then do something when I'm not running live?

I also coudln't figure out how to install it because you need the desktop to do so... which I didn't have.

So what does everyone recommend I do... try to fix it so it works regularly off the live disc(which I would need help doing) or just go ahead and install it and get the GUI working that way (which I would also need help doing).

---

### Post by Aaron Kupniewski on 2006-06-16
I've been tinkering around on the live disc, and I still can't get the GUI to work without booting in safe graphics mode.  Does anyone know how I can fix this because I need to know if I can get ubuntu's GUI to work when I fully install it.

---

### Post by The Cosmic Hobo on 2006-06-16
I could get the live CD to boot normally, but unless I booted it in safe graphics mode, the installer would hang. My suggestion would be to just try installing it, you can always remove it or tinker with your graphics settings when it's installed.

---

### Post by brentoboy on 2006-06-16
you probably have a video card driver issue.  install in safe mode, and touble shoot later. if all else fails you can use the vesa drivers for the installed system instead of the ones that should be working but arent.

---

### Post by Aaron Kupniewski on 2006-06-16
Yah, but I did the same thing with debian and I was never able to get the GUI working on that.  Would anyone here be able to help me out with getting the GUI up and running because I had little help with debian.

---

### Post by brentoboy on 2006-06-16
how far did you get?

---

### Post by Aaron Kupniewski on 2006-06-16
Oh well with debian the furthest I got was just using the vesa drivers which didn't prove to be too satisfactory.

The nvidia drivers that I tried to get didn't work at all, they didn't even install.

---

### Post by brentoboy on 2006-06-16
well, lets get ubuntu going with the vesa drivers, and then if you want to, we can get the drivers from nvidia's site up and working on your PC.  With the nvidia 6200 chipset that worked best for me (under breezy).

I've done it several times.

---

