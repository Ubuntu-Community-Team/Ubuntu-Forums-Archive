---
title: "I want to reinstall OS X"
date: 2005-08-19
forum: Apple PPC Users
---

### Post by Aerolite on 2005-08-19
Well, I originally wanted to use Ubuntu for my dual usb iBook 3 as its only OS...And I've been using it for quite some time.  But now, I want to revert to OS X and OS X only.  However, my OS X installation disc won't read.  Is there something that I'm doing wrong?  I was never too good with Ubuntu or Linux for that matter...Just thought it would be something nice to learn as I used it.  But now I don't have the time and would like to go back to the way it was.

---

### Post by kvidell on 2005-08-19
[QUOTE=Aerolite]Well, I originally wanted to use Ubuntu for my dual usb iBook 3 as its only OS...And I've been using it for quite some time.  But now, I want to revert to OS X and OS X only.  However, my OS X installation disc won't read.  Is there something that I'm doing wrong?  I was never too good with Ubuntu or Linux for that matter...Just thought it would be something nice to learn as I used it.  But now I don't have the time and would like to go back to the way it was.[/QUOTE]
 Pop in the CD, reboot, and hold the "C" button I believe it is, to boot from the CD.

HTH,
- Kev

---

### Post by pierba on 2005-08-20
You can, also, write this line:
enablecdboot
in your /etc/yaboot.conf,
run:
sudo ybin
and at rebooting you are able to boot by cd.

Pietro

---

