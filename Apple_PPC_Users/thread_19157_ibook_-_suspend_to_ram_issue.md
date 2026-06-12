---
title: "ibook - suspend to ram issue"
date: 2005-03-10
forum: Apple PPC Users
---

### Post by Xappe on 2005-03-10
i've installed Hoary on an ibook g3 (think it's ibook 2). the thing is now, that it won't wake up after it's down sleeping (close the lid --> sleep --> open the lid --> dead).

i've tried the scripts suggested at the ppc section of this forum and at bugzilla, but no go.

it would be nice to know if there are any plans for implementing kernel patches soon, or if I'll have to live with no sleep, or maybe an howto that tells people how to patch the kernel themselves...

or other suggestions.

---

### Post by mikji on 2005-03-27
I'm suffering the same problem.

If anyone has any ideas, please speak up!

---

### Post by beb0s on 2005-03-27
see ubuntu bug 1940 on bugzilla

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1940](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940)

or this message on debian mailing list

[http://lists.debian.org/debian-powerpc/2005/01/msg00382.html](http://lists.debian.org/debian-powerpc/2005/01/msg00382.html)

bye

---

### Post by diabolo on 2005-03-28
Also take a look at the scripts grover posted in this Ubuntu forum thread:
[http://ubuntuforums.org/showthread.php?t=2368](http://ubuntuforums.org/showthread.php?t=2368)
That's what I used to solve the problem.

---

### Post by mikji on 2005-03-30
Unfortunately, I've tried stopping dbus and hal, then sleeping it. It doesn't work with hoary's kernel (2.6.10), but it does work with warty's kernel (2.6.8). So right now I'm using hoary with warty's kernel, but I'd still like to solve the problem. Any other suggestions? Again, I've tried the dbus/hal solution with the newer kernel, and it no longer works.

Thanks.

---

### Post by blackfede on 2005-04-27
I made it!!  :razz: iBook G4, 1Ghz!
I found a page, [http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-7.html](http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-7.html) that say disable DRI for Xorg, remove some modules made all work. More detail on that page. Now, i rmmod'ed manually the modules, how i can do it automatically, when i close the screen? And how i can reload them after i wake up?

---

### Post by gruepig on 2005-04-27
[QUOTE=mikji]Unfortunately, I've tried stopping dbus and hal, then sleeping it. It doesn't work with hoary's kernel (2.6.10), but it does work with warty's kernel (2.6.8). So right now I'm using hoary with warty's kernel, but I'd still like to solve the problem. Any other suggestions? Again, I've tried the dbus/hal solution with the newer kernel, and it no longer works.

Thanks.[/QUOTE]

Same here (14'' white iBook G3, PowerBook4,3).  I've tried the dbus/hal fixes (both /etc/power/scripts.d/ and /etc/apm/scripts.d), disabling various kernel modules, X, etc, but have had no long with hoary's kernel.  My iBook intermittently wakes up from sleep, but usually gives varying errors (airport, gpm, no hard drive, no getty, no gnome-panel, kernel errors, etc.)  The 2.6.8 kernel works fine (with the dbus/hal fix), so that's what I'm using.  Does anyone have a working config for 2.6.10 on the iBook G3?

---

### Post by blackfede on 2005-05-01
After some trying i have fount that DRI in xorg was the issue of freeze in wakeup phase. So if you want to sleep your iBook G4 edit the config file of Xorg, and comment out the line of DRI. This worked for me, whitout removing modules by hand. All the script made the work for you. :)

---

### Post by callipeo on 2005-05-01
[QUOTE=blackfede]After some trying i have fount that DRI in xorg was the issue of freeze in wakeup phase. So if you want to sleep your iBook G4 edit the config file of Xorg, and comment out the line of DRI. This worked for me, whitout removing modules by hand. All the script made the work for you. :)[/QUOTE]

Hi,

can you check if the solution posted in [http://ubuntuforums.org/showpost.php?p=139484&postcount=40](http://ubuntuforums.org/showpost.php?p=139484&postcount=40) works for you? That should make it possible to suspend the iBook even with DRI enabled.

---

### Post by gruepig on 2005-05-01
[QUOTE=blackfede]After some trying i have fount that DRI in xorg was the issue of freeze in wakeup phase. So if you want to sleep your iBook G4 edit the config file of Xorg, and comment out the line of DRI. This worked for me, whitout removing modules by hand. All the script made the work for you. :)[/QUOTE]

The (white) iBook G3 has a different problem than the iBook G4. The iBook G3 has intermittent problems even when X is not running.

---

### Post by Xappe on 2005-08-23
how about breezy? any news on suspend to ram for ibooks there?

---

### Post by callipeo on 2005-08-23
[QUOTE=Xappe]how about breezy? any news on suspend to ram for ibooks there?[/QUOTE]

I have seen two major improvements with my laptop (iBook G4): the sound card does not scratch anymore on wake up, and I can put the laptop to sleep with a USB device attached.

I don't know the situation of the G3 iBooks; I guess it would be the best if someone who owns such a laptop would try with breezy by itself. Last time that I checked breezy seemed pretty stable, excluding the installation.

---

### Post by Xappe on 2005-08-23
excluding the installation? so a dist-upgrade from hoary would be the way to go right now then?

---

### Post by callipeo on 2005-08-23
[QUOTE=Xappe]excluding the installation? so a dist-upgrade from hoary would be the way to go right now then?[/QUOTE]

In my experience, yes, this is the way to go. I have installed hoary in a spare partition - and then upgraded to breezy - several time in the past months without much trouble. Of course this means that you cannot report bugs against the installer, but if  your goal is to quickly test the suspend to ram status I would go this way.

---

### Post by Xappe on 2005-08-23
thanks. maybe I'll give it a try in the next couple of days. The ibook is mainly for playing around with linux anyway since it no longer contains even a trace of osx :)

---

### Post by callipeo on 2005-08-23
[QUOTE=Xappe]thanks. maybe I'll give it a try in the next couple of days. The ibook is mainly for playing around with linux anyway since it no longer contains even a trace of osx :)[/QUOTE]

Well, the main issue I have found in the installer (which prevented the installation to complete) was related to the automatic detection of the installed OSes, particularly regarding the HFS partitions. If the only OS installed is linux, maybe you could try the colony #3 CD. Stay in guard anyway :-)

---

### Post by Xappe on 2005-08-23
now i'm up and running breezy on the ibook. suspend to ram still does not work properly, at least not from scratch. It sleeps, but hangs on wake up. i'll look into that more in the next couple of days I guess...

cheers

---

### Post by Xappe on 2005-08-24
ah, nice. I can get the ibook to suspend in breezy using the hal-script :)

---

### Post by RIVE on 2005-09-14
I have a iBook G3 500 mhz using breezy, i can't make it sleep, where are those hal-scripts to try it?

---

### Post by Xappe on 2005-09-14
[QUOTE=RIVE]I have a iBook G3 500 mhz using breezy, i can't make it sleep, where are those hal-scripts to try it?[/QUOTE]

[http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39) 


the name of the dbus service has changed in breezy, so you will have to change the references in the script from /etc/init.d/dbus-1 to /etc/init.d/dbus.

---

### Post by RIVE on 2005-09-14
[QUOTE=Xappe][http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39) 


the name of the dbus service has changed in breezy, so you will have to change the references in the script from /etc/init.d/dbus-1 to /etc/init.d/dbus.[/QUOTE]
 Thank you for the info Xappe, suspend to ram now works in my iBook.

Muchas Gracias :)

---

