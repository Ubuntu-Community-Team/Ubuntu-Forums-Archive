---
title: "Alert! /dev/hda1 does not exist"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by philly_newwbie on 2006-09-27
Absolute nebie here from the world of windows but ready to move over to ubuntu-

Problem starts after update two days ago.  
1) First error is optical dice could not be found
2) then followed with waiting for root file system
3) then alert! /dev/hda1 does not exist dropping to a shell.
4) then show /bin/sh: can't access tty; job control turned off

I can not boot from the ISO image that was downloaded.  Even on the BIOS (Dell Inspiron 800, P3, 256mb ram) there is no cd rom present.

Any pointers would be greatly appreciated.. Thanks

---

### Post by bodhi.zazen on 2006-09-27
Ouch... Sounds like a hardware problem......

---

### Post by oly on 2006-12-03
I came accross this problem, and in my case it seems to be caused by the primary hard drive being pluged into the secondary master slot on the mothernoard.

moving it to the primary master slot allowed the pc to boot, this happened with dapper and edgy.

---

### Post by smoker on 2006-12-03
> Even on the BIOS (Dell Inspiron 800, P3, 256mb ram) there is no cd rom present.

sounds like your cd-rom is faulty, try checking the cables, try swapping it out if you have another one handy

---

