---
title: "USB/Firewire drive with HFS+ filesystem Read-only"
date: 2008-08-23
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2008-08-23
(I posted this in Amd64 category, before finding the Apple Users' forum here)

I have a Verbatim Firewire/USB drive formatted as HFS+,
It's read-only despite being mounted read-write:
/dev/sdb3 on /media/firewire type hfsplus (rw,nosuid,nodev,uhelper=hal)

So even mounted with the above settings, it's still only read-only:

sudo touch /media/firewire/x
touch: cannot touch `/media/firewire/x': Read-only file system

Same problem occurs whether I use USB or IEEE 1394.

It's writable from OS X...

---

### Post by tiresia on 2008-08-23
How have you formatted that Drive? 
Have you used Apple Disk Utility with the option HFS+ Journaled?
Linux does not support writing on HFS+ Journaled 
You may want reformatting it (with Apple Disk Utility) as HFS+ (not Journaled)

---

### Post by cyberdork33 on 2008-08-23
> **tiresia said:**
> How have you formatted that Drive? 
Have you used Apple Disk Utility with the option HFS+ Journaled?
Linux does not support writing on HFS+ Journaled 
You may want reformatting it (with Apple Disk Utility) as HFS+ (not Journaled)
Yes journaling is your problem, but you do not need to reformat:
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

