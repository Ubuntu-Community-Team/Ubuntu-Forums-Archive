---
title: "Problems with starting 7.04 on iMac"
date: 2007-05-28
forum: Apple Intel Users
---

### Post by mishad7 on 2007-05-28
I have iMac 20" Core 2 Duo, and a working 7.04 installation (the disc is ok, I verified it). Btw, I should say that I am a newbie when it comes to Linux, and that my original plan was to dualboot Ubuntu and Mac OS X (by creating a Boot Camp partition and installing ubuntu without Swap partition - read somewhere on this forum; if you think that is not smart, please respond). But I cannot pass the first step - starting Ubuntu form a Live CD. 

When I start my computer from a CD (using ALT), an Ubuntu menu appears, and I select the first option. So, everything loads, few black screens with some text, and then an error appears. I don't remember what it says, but I remember that it was in a blue window, and some X program made the error (sorry for the terms used, but I really don't remember). Anyone has any ideas how to start/install this thing?

Thanks in advance!

EDIT: Btw, if you know a good guide for installing Beryl so that it works with my graphic card, please copy the link.

---

### Post by incubus on 2007-05-28
mishad7,

It would be very helpful if you could give us more specific details.  One thing I sometimes do is to use a camera to take a picture of the screen.  But anyway, it seems to me that the installer can't start the X server, that is, the graphical interface.  I can see two options here.

1. You could give us more specific details and we can try to debug.  For example, if the problem is the resolution, you could try to edit /etc/X11/xorg.conf and correct it manually.  Can you go to a different terminal by pressing CTRL+ALT+F1 or F2?  If you can, the log file is /var/log/Xorg.0.log

2. Instead of using the Live CD, with graphical installer, you could try the alternate CD.  That's usually what I do and it's pretty easy to follow (it will be basically the same thing).

Let us know!

incubus

---

### Post by ronocdh on 2007-05-29
As incubus has already encouraged you to do, please give more hardware information! The iMacs in particular are a tricky bunch, because depending on the era, one can have either an ATI or an Nvidia card. In light of what you've said has gone wrong, though, I think you've an ATI card and you're failing to start X, just like the rest of us.

Incubus is right to recommend you use the alternate installer CD (I always do), but nonetheless you'll have to correct the X server issue at some point. With the live/desktop CD you'll have to correct it before you install, with the alternate, after. Later is always better, no? ;)

Check my sig for a link on the X failure. I also have one on Beryl which works swell on my ATI X1600 Radeon Mobility. I'd be interested to hear your results with hardware, too, please.

---

### Post by mishad7 on 2007-05-29
Hey,
Thank you all, but it seems to be working now. I restarted my computer, started the live cd form rEFIt (and not holding ALT like I did the first few times), and it magically worked. Maybe it was pure luck, or it worked thanks to rEFIt, but I am a happy new ubuntu user!

---

