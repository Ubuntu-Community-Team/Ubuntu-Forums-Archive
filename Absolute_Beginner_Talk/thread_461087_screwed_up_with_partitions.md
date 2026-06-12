---
title: "screwed up with partitions"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by soldierx on 2007-06-01
ok guys, im a n00b, i installed Ubuntu 7.04 today with Windows Xp Pro

its dual boot, everything went fine and everything works fine except i screwed one thing up!!

i accidentally made my 80gig HDD into 20gigs for WINXP and 60 for Ubuntu, which i didnt want, i wanted 20gigs for ubuntu. Is there a way of correcting this?

thanks:)

---

### Post by jonward0690 on 2007-06-01
Boot with the live cd and use the partiton manipulater to make them the size you want

---

### Post by drowner on 2007-06-01
> **soldierx said:**
> ok guys, im a n00b, i installed Ubuntu 7.04 today with Windows Xp Pro

its dual boot, everything went fine and everything works fine except i screwed one thing up!!

i accidentally made my 80gig HDD into 20gigs for WINXP and 60 for Ubuntu, which i didnt want, i wanted 20gigs for ubuntu. Is there a way of correcting this?

thanks:)

Yes. Did you install with the LiveCD?

Boot from the liveCD and run gParted. You should be able to manipulate the partitions.

---

### Post by soldierx on 2007-06-01
thanks for quick reply

im in the partitioner and i dont know how to allocate so that my windows partion is 60gb and linux is 20

---

### Post by drowner on 2007-06-01
> **soldierx said:**
> thanks for quick reply

im in the partitioner and i dont know how to allocate so that my windows partion is 60gb and linux is 20

First things first:
You are running the live cd, right?

---

### Post by soldierx on 2007-06-01
yep

---

### Post by drowner on 2007-06-01
> **soldierx said:**
> thanks for quick reply

im in the partitioner and i dont know how to allocate so that my windows partion is 60gb and linux is 20

You are running gParted?

Select the linux partition, it is normally formatted ext3, and resize it

Then select the windows partition, probably formatted NTFS, and resize it.

---

### Post by drowner on 2007-06-01
Oh, and i hope you've backed everything up.

Back everything up.

---

### Post by soldierx on 2007-06-01
i made the linux one 20 gigs, now when i try to resize the windows one says max size 20gigs, and it wont let me make it 60

---

### Post by Golyadkin on 2007-06-01
I had the same problem when installing Ubuntu as a second OS next to XP, the interface is unclear on what part of the partition is going to be the Ubuntu space. I know it says there in the small text, but who reads that anyway? Using color and graphics, this should become much easier.

Also btw, I tried to boot from the Live CD and run gparted to fix it, but the partition was non resizable. The only option left for me was to reinstall both operating systems. (Luckily they were both clean installs, so no real work lost there).

---

### Post by soldierx on 2007-06-01
i reckon hey, i really cant be bothered reinstalling xp and ubuntu again

---

