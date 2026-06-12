---
title: "Odd Grub Error"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by uber on 2006-07-28
So I'm pretty new to this whole Linux thing (as everybody here is, I would guess), and I'm experiencing an odd problem that I would like to know how to fix.

I downloaded the x86 Live CD from the Ubuntu web page, mounted it and installed Dapper on a new WD Cavair SATA 160 GB HD. Everything went smoothly and perfectly throughout the install process. I reboot, remove the CD and when starting I get an error message that says something like this:

Error Grub 17.

The really odd thing is that when I choose to instead boot from the Live CD, and select "Boot from first Hard Disk," I get a menu asking me which operating system I would like to boot (I have XP SP2 installed on a different IDE drive) and from there everything works perfectly. 

As well, if I don't have the SATA drive configured as a JBOD in the BIOS settings I get a Grub 21 error instead of a 17. 

So my question to all the masters out there is, what is going on, and, how do I fix it?

---

### Post by s_h_a_d_o_w_s on 2006-07-28
check out this thread, though it's for gentoo, it might help.

[http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)

:-)

---

### Post by uber on 2006-07-28
Interesting, I've tried setting the BIOS up to boot from the SATA drive, but that hasn't worked at all. I'll try some of the GRUB configuration stuff when I get home later tonight. 

On a side note, does anybody know why my BIOS would be unable to recognize the drive until I had it formatted as a JBOD?

---

