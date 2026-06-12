---
title: "DVD problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by themaceisback on 2007-08-20
I installed ubuntu server 7.04 a couple of days ago, and i went to install some stuff on a dvd it wouldn't recognise it. It plays cds fine, but when i go to mount the dvd i gives me a "no media found". I have tried other dvds also with the same result. It is a dvd player but it just isn't working. 

P.S. i have 2 disk drives, ubuntu recognises them and they are both in /media but i can only find the corrisponding file in /dev for one of them(which is cdrom)

---

### Post by jakev383 on 2007-08-20
Are you sure it's not the drive?  I have a DVD/CDWriter in my system that one day decided to stop reading DVDs.  It still works as a CDRom and a CDWriter, but will not recognize DVDs.  I've tried several other LiveCDs just to make sure that I didn't bork something, and all that did was to confirm that the drive decided it did not like to do 2 jobs, and decided to only be a CD.

---

### Post by hyper_ch on 2007-08-20
When you insert the dvd, normally you should get some LED flashing and so on... does this happen when you insert the dvd (you may compare it with inserting a cd).

---

### Post by asmoore82 on 2007-08-20
> **themaceisback said:**
> I installed ubuntu server 7.04 a couple of days ago, and i went to install some stuff on a dvd it wouldn't recognise it. It plays cds fine, but when i go to mount the dvd i gives me a "no media found". I have tried other dvds also with the same result. It is a dvd player but it just isn't working. 

P.S. i have 2 disk drives, ubuntu recognises them and they are both in /media but i can only find the corrisponding file in /dev for one of them(which is cdrom)

I think I know the problem but not sure how to fix on modern systems...

The problem is that DVD means 2 things:
1. it is a type of physical disk, which can hold 4.7 GB on a single layer.
2. it is movie format encapsulated in UDF format, which is sideways compatible
with the old ISO CD-ROM format.

So, when you just want to store some data on a DVD, you typically use the
old CD-ROM format on a physical DVD disk. Linux needs to know that even
though it is a DVD disc, it should be mounted as a CDROM ( -t iso9660 ) ...

On older Linux system, having a DVD combo drive meant that you had 2 devices under "Computer"
one that always used UDF and the other always used ISO.

now that my long-winded backstory is over, I will have to defer to someone else for a
proper Ubuntu fix for the situation if it is indeed the problem.

If all else fails you could always split the /etc/fstab entry and go old school...
changing this 1 line
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
into these 2 lines
```
/dev/scd0       /media/cdrom0   iso9660 user,noauto     0       0
/dev/scd0       /media/dvd0   udf user,noauto     0       0
```
but only as a last resort.

---

