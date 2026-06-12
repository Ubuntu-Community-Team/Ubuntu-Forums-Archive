---
title: "G3 Bondi-Live"
date: 2006-01-09
forum: Apple PPC Users
---

### Post by Paradise on 2006-01-09
Hey there,
     I am workin' on a way to reuse some old 333mhz Bondi iMac's for a school.  I pulled down Breezy Badger-Live and can not get past the sound that plays when you boot.  While the screen is black I can randomly hear the CD drive spin up then down.

     Any suggestions on how to get this computer up?


P:confused:

---

### Post by linear on 2006-01-09
Sounds like incorrect settings in xorg.conf.

Try the following, after booting is complete:
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/kdm restart (return) to restart KDE

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart KDE and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

Problem with the LiveCD is that you need to do this every boot. Hope you plan to do an install to the hard disk.

---

### Post by Paradise on 2006-01-10
Tx for the excellent input.  Now that I have command line acess I determined I am running gnu and not kde(at the top of the edit window).

I will install just as soon as I check out the Badger experience.

So, I am now stuck at the sudo /etc/init.d/kdm since I acutally need to resart gnome.  Should I move my post to the Gnome forum?


:rolleyes: gettin' better!

P

---

### Post by linear on 2006-01-10
> So, I am now stuck at the sudo /etc/init.d/kdm since I acutally need to resart gnome.

Easily fixed - just type **sudo /etc/init.d/gdm** instead.

---

### Post by Paradise on 2006-01-10
Linear... your awesome!  My desktop is now on, but the wndows are not drawn correctly.  The bar at the top has shards of a life preserver and a world; although the clock is showing up ok.  The bottom has a desktop icon in the lower left, and four brown boxes and a blue thing in the lower right.  Is this the result of the "slowness" you mentioned?

Lastly, I put a different flavor of LINUX on the HD.  Can I inst. Ubuntu ontop?  Format the drive first?

Nearly perfect now...;) 

P

---

### Post by linear on 2006-01-10
Not sure about the appearance of your screen - the bottom sounds OK, but icons that look like "shards" are a little strange. You could always try other default color depths in xorg.conf to see if it makes any difference.

You would know the slowness if you saw it - you'd think the computer had locked up.

It'd be safer and cleaner to wipe the disk first, since it sounds like you don't need the other distro. No idea what the installer does if it finds another Linux there.

---

### Post by Paradise on 2006-01-23
Ok,
     I installed a 256 SODIMM and verified a 6M video ram chip.  Blew away the HD, installed 9.2.2 and rebooted from Badger.  Now my video is perfect.  Tx Linear for all the help.
     Starting a new thread on Install of badger from Live...


P:p

---

