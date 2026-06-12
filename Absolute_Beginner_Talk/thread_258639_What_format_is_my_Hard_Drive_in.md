---
title: "What format is my Hard Drive in?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-16
I am running Ubuntu 6.06 which was initially setup by another person.

I am now curious about installing NFS and so I need to know what my hard drive is formated in?  

Any ideas on how I can discover the partition/drive's format?

Thanks

---

### Post by MrHorus on 2006-09-16
> **Calculator said:**
> I am running Ubuntu 6.06 which was initially setup by another person.

I am now curious about installing NFS and so I need to know what my hard drive is formated in?  

Any ideas on how I can discover the partition/drive's format?

Thanks

Ext3, or Third Extended.

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by djsroknrol on 2006-09-16
Go to:

System>Administration>Disks

You should find everything you need there...

---

### Post by Najand on 2006-09-16
It is usually "Ext3", but if you are unsure you can use 
"mount" command to see what is your hard disks type.

---

### Post by Calculator on 2006-09-16
Thanks 

Ext3 it is - in RAID 1.

:D

---

### Post by mongooseman1128 on 2006-09-16
it's probably in that format, but for future reference Gnome partition editor is really simple for looking up the formats of all your partitions. I don't remember exactly where it is right now (I'm on my XP install instead of linux), but I think it's under system > administration or something to that effect

---

