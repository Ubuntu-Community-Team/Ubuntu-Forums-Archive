---
title: "Visioneer OneTouch 5800 USB Scanner"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-03
I could never get this scanner to work with XP. If this would work under ubuntu, I would be a happy camper. Anyone know if this is supported, or if there is a resource I can check?

EDIT: Installed sane-utils, ran sane-find-scanner, and got 
found USB scanner (vendor=0x04a7, product=0x0226) at libusb:001:007

So, I just need to figure out how to use it, looks like its connected right

---

### Post by FleetAdmiral74 on 2007-06-03
$ sudo --bump-to-top

---

### Post by the.phantom on 2007-06-03
i am not a expert !!!
but i just got my scanner working the other day !
my xp one was not on the sane list so it just sat there

but this one was
so what i did 
hot plugged the usb cable and waited about 15 sec for U to see what was going on

applications/Graphics/Xsane image scanner

and it came up ( never did in old scanner) and it found my scanner so it went right to a "scanner interface" and figured how to work it
i can only get 600dpi but that is way good enough for me 
this might help on the interface
[http://www.xsane.org/doc/sane-xsane-viewer-doc.html](http://www.xsane.org/doc/sane-xsane-viewer-doc.html)

and on the right side i had a window i could crop and not have it scan the full 8 X 11 for a small image

NOTE: just a hint, might wait a bit longer than 25 min before bumping your post, this is a bit busy of a place, most give it a day

---

### Post by FleetAdmiral74 on 2007-06-03
when I do that, it says no devices available. yet it is detected with the command I mentioned earlier. Not quite sure how to procede. I dl'ed the drivers from their site (windows only btw), installed with wine, but the exes created do not run. I was hoping I could just use them, but nothing comes up.

---

