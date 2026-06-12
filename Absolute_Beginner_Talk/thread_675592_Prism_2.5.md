---
title: "Prism 2.5"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by mjheagle8 on 2008-01-22
My prism 2.5 wireless card is not working.  The status says disabled.  I followed the instructions to make it use the hostap driver but when i run lshw -c network (or something like that I forgot) it says the the name of the wireless card then DISABLED while my ethernet port is enabled.  How do I enable the wireless card?  It is an d-link intersil prism 2.5.  Thanks!  (I am an ubuntu n00b)

---

### Post by spiderbatdad on 2008-01-22
try```
ifdown eth1
```

---

### Post by mjheagle8 on 2008-01-23
that code did not work.  I need to know how to enable the wireless card.  thanks!

---

### Post by deltaprime on 2008-01-23
to enable the driver check what the name of the driver is
this is an example for the intel 3945 card which uses the driver ipw3945
so i am now giving you the commands how to load the card. for yourself replace the ipw3945 with the name of your driver


**sudo modprobe ipw3945**

to unload:

**sudo modprobe -r ipw3945**


hope this works keep me updated

DELTA

---

