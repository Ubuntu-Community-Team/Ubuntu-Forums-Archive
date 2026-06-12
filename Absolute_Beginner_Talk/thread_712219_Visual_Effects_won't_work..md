---
title: "Visual Effects won't work."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by XxBigP123xX on 2008-03-01
Okay, i haven't used linux in a while so bear with me here.:lolflag:

Im  trying to activate the visual effects (system-preferences-appearance) but every time i turn it on it wont work even when i just click normal. Help?

---

### Post by Golem XIV on 2008-03-01
Do you get any error message?  What are your system specs (especially your video card)?

---

### Post by XxBigP123xX on 2008-03-01
> **Golem XIV said:**
> Do you get any error message?  What are your system specs (especially your video card)?

Mobile Intel® 965 Express Chipset Family. and the error is "Dekstop effects could not be enabled".

---

### Post by owbizi on 2008-03-01
Well, probably it's blacklist/whitelist problem...

Type compiz on terminal, and post here what you get. :)

---

### Post by mason215 on 2008-03-01
i was wondering also why when i put on desktop effects it automatically logs me out every time

---

### Post by owbizi on 2008-03-01
Weird... what's your video card? Do you have restricted drivers enabled?

---

### Post by mason215 on 2008-03-01
> **owbizi said:**
> Weird... what's your video card? Do you have restricted drivers enabled?

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

yeah i have restricted drivers enabled

---

### Post by XxBigP123xX on 2008-03-01
> **owbizi said:**
> Well, probably it's blacklist/whitelist problem...

Type compiz on terminal, and post here what you get. :)

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 


```

How do i enable restricted drivers?

---

### Post by Rolcol on 2008-03-01
Settings > Administration > Restricted Drivers Manager > Check the box of any devices you wish to enable restricted drivers.  It may ask to download the drivers.

---

### Post by Joeb454 on 2008-03-01
It sounds like it could be an issue with blacklisted drivers, because I have an intel chip (no nvidia/ati card) and I have compiz enabled :)

---

### Post by XxBigP123xX on 2008-03-01
> **Rolcol said:**
> Settings > Administration > Restricted Drivers Manager > Check the box of any devices you wish to enable restricted drivers.  It may ask to download the drivers.

It says "Your computer doesn't need any restricted drivers" :(

---

### Post by owbizi on 2008-03-01
> **XxBigP123xX said:**
> Mobile Intel® 965 Express Chipset Family. and the error is "Dekstop effects could not be enabled".

Well, from [here](http://becomingaccie.blogspot.com/2008/02/unblacklist-intel-965-from-compiz.html), open a terminal and:
$ sudo gedit /usr/bin/compiz

Comment out this line (put a # on the start of it):
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965

Save and exit. After, still on terminal:
$ gksudo gstreamer-properties

And, on video tab, select the default output plugin as:
X Windows System (X11/XShm/Xv)

Hope it helps. :)

---

### Post by owbizi on 2008-03-01
> **mason215 said:**
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

yeah i have restricted drivers enabled

It seems that you have to configure UniChrome's drivers to run Compiz. Take a look [here](http://ubuntuforums.org/showthread.php?t=701987) and [there](http://ubuntuforums.org/showthread.php?t=624045)!

---

