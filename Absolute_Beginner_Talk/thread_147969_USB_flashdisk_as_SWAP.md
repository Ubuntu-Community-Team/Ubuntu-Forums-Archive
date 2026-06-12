---
title: "USB flashdisk as SWAP ?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by joris_xl on 2006-03-21
Hi very fresh to Ubuntu but was wondering if my old DELL inspiron 4000 would do OK with little RAM but USB flashdisk as SWAP for Ubunti ????:confused: 
Howto...
Thanks, Joris.

---

### Post by taurus on 2006-03-21
It should be fine AS LONG AS the kernel sees it as the same device, /dev/sda1!  Otherwise, the system would get confused when it tries to activate swap from /etc/fstab!

---

### Post by steve.horsley on 2006-03-21
I'm not convinced this is a good idea. As far as I know, flash has a limited number of write cycles, and using it as swap space could soon use this up. And I think that flash may prove a little slower than you might want for swap space.

---

### Post by joris_xl on 2006-03-21
Yes, was thinking about the write cycles but didn't think it so serious; thanx. But system is VERY slow with insufficient RAM so was thinking... anything else... ?  

Anyhow WINXP was doing OK and trying to remove Ubuntu partition,
screwed up GRUB and partition table or something alike, 

so nothing starting any longer, reinstalled only Ubuntu... :-D      DEAD SLOW...  
try to recover something from my Windows partition which doesn't show any more...

---

### Post by mcduck on 2006-03-21
As the previous writer told, using Flash for swap is not a good idea. Anyway, your hard disk is much faster than any flash memory..

---

