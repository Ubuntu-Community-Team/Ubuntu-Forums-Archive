---
title: "Impossible to switch screen resolution on iMAC CRT"
date: 2005-04-04
forum: Apple PPC Users
---

### Post by catarano on 2005-04-04
Dear All

I am finding impossible to switch the screen resolution to 800x600
on the latest candidate elease of ubuntu
this won't happen even if in the xorg.conf file i force only one resolution
for instance in the screen section of the file i leave only one colour mode (16 bit) and only one resolution (800x600)
the thing doesn't change either specifing the monitor as an "iMac" or as a "generic monitor"
I have an ATI rage 128 Ultra, which is properly detected and things don't change even though i use either the "ati" drive or the "r128"
my vsync range is 60-60
and i have a refresh range 75-117
but even forcing a refresh of 95-95 only does not allow me to change resolution.
The only thing that the gnome control panel for setting up the screen resolution shows
is 1024x768 at 75 hz.
I did some grep searches to find the 1024x768 string but i couldn't find anything.
How can gnome manage to override the xserver settings?
Has anyone managed to set up his7her screen resolution at the wanted values on a crt imac?
Thanks

---

### Post by chascon on 2005-04-11
look in the warty specific forum postings concerning "Rage 128 and accel" or "Rage 128 and DRI" for an xorg.conf I posted.  Or just find all postings I posted, and work from there.

---

### Post by everettattebury on 2005-06-09
[QUOTE=catarano]Dear All

I am finding impossible to switch the screen resolution to 800x600
on the latest candidate elease of ubuntu
this won't happen even if in the xorg.conf file i force only one resolution
for instance in the screen section of the file i leave only one colour mode (16 bit) and only one resolution (800x600)
the thing doesn't change either specifing the monitor as an "iMac" or as a "generic monitor"
I have an ATI rage 128 Ultra, which is properly detected and things don't change even though i use either the "ati" drive or the "r128"
my vsync range is 60-60
and i have a refresh range 75-117
but even forcing a refresh of 95-95 only does not allow me to change resolution.
The only thing that the gnome control panel for setting up the screen resolution shows
is 1024x768 at 75 hz.
I did some grep searches to find the 1024x768 string but i couldn't find anything.
How can gnome manage to override the xserver settings?
Has anyone managed to set up his7her screen resolution at the wanted values on a crt imac?
Thanks[/QUOTE]

I'm having the exact same problem, I wonder if anyone has figured it out.  Catarano, have you had any luck using headphones with your iMac?

---

### Post by charon79m on 2005-10-24
I am having this issue too.

Anyone have a solution here?

Mike K.

---

### Post by ULffuntu on 2005-12-17
Complete frustration here after hours of tweaking xorg.conf. Breezy on iMac SUCKS

---

