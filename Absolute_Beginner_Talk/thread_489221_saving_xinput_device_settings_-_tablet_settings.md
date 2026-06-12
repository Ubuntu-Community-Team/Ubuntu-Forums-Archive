---
title: "saving xinput device settings - tablet settings"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by stil on 2007-07-01
heya

I prefer using this mode for my tablet...

> xsetmode stylus RELATIVE

Each time I reboot it resets to ABSOLUTE. I've tried playing around with xorg.conf but I don't really know what I'm doing.

I added this under the stylus section

> Option  "xsetmode"  "RELATIVE"

No luck tho!

How do I go tabout setting this up automatically?

---

### Post by stil on 2007-07-01
bump

---

### Post by Raineer on 2007-07-01
Unfortunately I am not familiar enough with the Stylus settings in Xorg to know the correct way to set it there.

However, I would think adding "xsetmode stylus RELATIVE" in the /etc/rc.local file would accomplish the same thing?  Sort of a hack but it should at least get you by until you can see how it works in xorg.  

rc.local is where I have my initialization commands for my G15 keyboard LCD display and it's never missed a beat.

---

### Post by stil on 2007-07-01
I'm not familiar with that file at all, but I'll give it a shot. Thanks.

---

### Post by Raineer on 2007-07-01
In layman's terms....it's just an "autoexec.bat".  Whatever commands you place in that file will be run on every boot.

---

### Post by stil on 2007-07-01
Sweet. Thanks again.

btw there wont be any issue with permissions when chaning this file?

---

### Post by Raineer on 2007-07-01
It's owned by root and run that way, so just use **sudo nano /etc/rc.local** like you did when changing xorg.conf

---

