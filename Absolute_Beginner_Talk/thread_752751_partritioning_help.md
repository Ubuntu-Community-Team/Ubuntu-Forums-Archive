---
title: "partritioning help"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Forgoten Dynasty on 2008-04-11
Im trying to install Ubuntu 6.10 using the text based installer

i have a 40 gig HDD

i want 10 gigs for windows
and the rest for ubuntu 

but i can not figure out how to get "swap" to work i tried making the mount point /swap but it wont work

can some one walk me threw it 

im pretty sure i gave my NTSF 10 gigs
but im not sure how or how much space to put in my other partritions

---

### Post by joshrobinson on 2008-04-11
swap needs no mountpoint
when your in the edit partition menu of the partition you want to be swap, when it says what filesystem type do you want, select swap, and that should be it

---

### Post by Forgoten Dynasty on 2008-04-11
i only get the options
primary and logical
:(

---

### Post by joshrobinson on 2008-04-11
so you have no partition for swap then? select primary, then set the size you want, then it will ask you what filesystem type you want, thats when you set swap

---

### Post by Forgoten Dynasty on 2008-04-11
OOOOOH lol im retarted thanks bro i got that but how big should i make my swap partision
right now i have 
K 10 NTFS
F 27 ext3 (i want his for ubuntu)
and 3 for swap (witch is F)

---

### Post by joshrobinson on 2008-04-11
the rule of thumb for swap is 2x your ram, say you have 512megs of ram, make it a 1gig partition, if you have 1 gig of ram, make it a 2gig partition and so on

---

### Post by Forgoten Dynasty on 2008-04-11
ohh ok so ill make it a gig
thanks alot

---

### Post by joshrobinson on 2008-04-11
your welcome

---

