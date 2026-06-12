---
title: "installing xp with ubuntu"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ryan73 on 2008-02-06
I have a acer laptop with 80 gig hard drive already portioned  into 40 and 40. I have xp running on one 40 and want to install ubuntu into the other 40. It appears some people have had issues with this. 

What are the steps to do this?
What issues should I watch out for?

I have been working the last couple of days backing up my system and making move in my system.

---

### Post by jan quark on 2008-02-06
the safest and easiest way is to install xp first

create a blank formated partition

and then install ubuntu into this partition 

see

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
and

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by airbornemist6 on 2008-02-06
With XP already installed boot from the linux livecd, click install, when it gets to the part where it asks about partitions, click manual, and delete the blank partition where you want to put ubuntu. Then in that space create an ext3 partition (about 39gb) which you will set as / and a swap partition (about 1 gb). From there you should be good.

---

