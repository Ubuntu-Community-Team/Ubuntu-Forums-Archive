---
title: "plug and play mouse"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Slavus on 2006-05-09
OK, so I get my USB mouse, plug it in, and it comes up with this:

device descriptor read/64 error --110-- anyone know what this means?

Also, when i boot, i notice it skips setting up the hotplug subsystem--Im guessing hotplug=plug n' play- is that the source of my problem?

I tried putting in the driver CD, but there is no autoplay and when I run setup.exe it says "unable to display media/cdrom1/mouse/setup.exe."

Unable to display? I want it to run, you silly goose 

I really want a mouse so I can browse the web on my powerhouse pc and not this windows 98 crap thing.

---

### Post by nanotube on 2006-05-09
well, i am not sure about this error thing you are getting, but this thread may be helpful: [http://www.ubuntuforums.org/showthread.php?t=48126](http://www.ubuntuforums.org/showthread.php?t=48126)

so basically, after you plug in your mouse, try opening a terminal and typing in
```
sudo modprobe -r ehci_hcd
```
and see if it starts working?

also, since you are trying to run a windows executable in linux, i take it you are pretty new here. :) thing is, you can't run windows programs in linux as if you were in windows.

---

### Post by Slavus on 2006-05-09
No, my mouse still isnt responding afterwards--
Im guessing that code is for usb harddrives and not mice?

---

### Post by nanotube on 2006-05-09
hmm, well, it was worth a shot. :) it was the only thing that seemed halfway related that i could find.
let's see if anyone more familiar with this stuff can suggest anything else.

by the way, maybe it's a hardware problem? have you tried using the same mouse under another system, or tried another mouse?

---

### Post by Slavus on 2006-05-09
Aye, that I have, but it seemed to be nothing more than a fluke

This thread can be closed because for some unknown reason, my mouse decided to work today-- happy days

---

### Post by nanotube on 2006-05-10
heh nice. :)

---

