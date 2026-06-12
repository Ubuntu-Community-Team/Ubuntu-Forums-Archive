---
title: "Double-Boot on a laptop"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by drinkmilk.ca on 2005-11-22
Ok well, I'll have a portable tomorow,
I wanna install Ubuntu (i've got version 5.04) and Win Xp on it...

Pentium 3  1000
dvd/cd player
hard disk : 20Gig 

I wanna make 3 partions : 5 gig linux, 5 gig winxp, 10 gig shared thing
and i want a double-boot thing...

i have linux on an other computer since a couple of month, but i don't understand all the command line thing.

and my windows install disk are stange... well... i have win xp but it's and update... so i always need to install win millenium before.

I have already format or split some drives

so what i was thinking to do is : 
-erase everything on the disk
-make one partion of 5 gig (fat) (C:\)
-install win millenium
-update to win xp
-put the ubuntu disk
-restart the computer
-boot from cd-rom
-start to install ubuntu till the place where we can make partition
-make a second partition of 5 gig (ext2)(D:\)
-finish to install ubuntu on that one
-ubuntu is suppose (i think) to detect i have win xp and make a double-boot via lilo.conf
-restart the computer
-boot from cd on win millenium cd
-chose ms-dos
-use fdisk to make the last partition of 10gig (fat)(E:\)

each time i try something that look like it will work... it never works so ... can you please tell me what's wrong with this ?

P.S. Scuse me if my english is incorrect but i'm french so... 

-Carl         (Drinkmilk.ca@hotmail.com)

---

### Post by gord on 2005-11-22
should be fine, apart from you can make the 'last' partition at the same time you make the ubuntu partition, just go into the manual partition menu. allthough, it is best you know what your doing (you look like you do).

---

### Post by drinkmilk.ca on 2005-11-22
I'll try this tomorow... thanks gord!

---

### Post by somody on 2005-11-22
Je pense que &#231;a marcherait bien.  Je suis aussi d'accord avec gord.  O&#249; vis-tu ?

---

### Post by aysiu on 2005-11-22
Install Windows first.
Then, follow these directions:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by drinkmilk.ca on 2005-11-22
Thetford Mines (quebec, canada)... si t'as msn : [email]drinkmilk.ca@hotmail.com[/email] ...

---

### Post by drinkmilk.ca on 2005-11-22
thank aysiu ... i'll read it carefully before doing anything !


p.s. this is the fastest forum i've seen!

---

### Post by aysiu on 2005-11-22
[QUOTE=drinkmilk.ca]thank aysiu ... i'll read it carefully before doing anything ![/quote] Let us know if you have any more questions--before you do something you're not sure of (rather than afterwards).

> 
p.s. this is the fastest forum i've seen! One of the only reasons I'm using Ubuntu instead of Mepis.

---

### Post by drinkmilk.ca on 2005-11-23
shit... i know there's was something wrong in my way of thinking... the windows millemium cd is an asshole... now... if i understand well... i'll have to 'low-level format' my harddrive... :???: i never did that before... my labtop is a IBM ... emm if someone have an other idea ?

---

### Post by d1337 on 2005-11-24
The Breezy installer will give you very nice options to shrink an existing partition.  Follow Aysiu's advice (especially installing MS first) and reads and you'll be golden.

d1337

---

### Post by aysiu on 2005-11-24
I don't know if I know what you're talking about...

Can you explain it again?

---

