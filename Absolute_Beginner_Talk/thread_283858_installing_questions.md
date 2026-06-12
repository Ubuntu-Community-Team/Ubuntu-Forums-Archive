---
title: "installing questions"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by thor908 on 2006-10-24
Is it possible to install ubutu onto my external hardrive and run it there? 
or can i install it to one of teh partitians of my hardrive? I didnt make them but one is like 40 gigabytes.... if so how would i boot from teh external harddrive or partition.

Any help is appreciated.

thanks

---

### Post by ReaderRat on 2006-10-24
How is your hard drive (internal) set up?
Please type into Terminal and run:
```
cat /etc/fstab
```
And post the output here.

---

### Post by brentoboy on 2006-10-24
this is a very tricky process, but I remember seeing it in this book last time I was at the bookstore:
Ubuntu Hacks: Tips & Tools for Exploring, Using, and Tuning Linux 

[http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1161733705/ref=pd_bbs_sr_1/104-3736306-3448751?ie=UTF8&s=books](http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1161733705/ref=pd_bbs_sr_1/104-3736306-3448751?ie=UTF8&s=books)

sorry I cant help any more.

the book is actually full of genuinly usable ideas (not just fluff)

---

### Post by ReaderRat on 2006-10-24
any luck?

---

### Post by thor908 on 2006-10-24
> **ReaderRat said:**
> How is your hard drive (internal) set up?
Please type into Terminal and run:
```
cat /etc/fstab
```
And post the output here.

terminal?
you mean teh run tool in windows? cause i tried that adn  was notld that cat/etc/fstab didn't exist...

---

### Post by ReaderRat on 2006-10-24
No, If you boot the LiveCD and let it get to the desktop, go to Applications>Accessories>Terminal and type in the code and press ENTER to get the printout. 
Then just Cut and Paste it here.

---

### Post by thor908 on 2006-10-24
i get...

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by thor908 on 2006-10-25
what doe all that mean?


unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

