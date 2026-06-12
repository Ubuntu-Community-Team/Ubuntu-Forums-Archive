---
title: "recover data [Resolved]"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-12-20
right since i dont seem to be able to fix my xserver on hda1,
is there a way i can mount hda1 from my second hard drive and extract all my data as there are some documents on there i cant afford to loose i have dapper on hda1 and i am using edgy on the second hard drive..

                                   thanks

---

### Post by Sef on 2006-12-20
I would use [Knoppix]("http://knoppix.com").  I was able to save documents off of a computer that would not boot up.

---

### Post by az on 2006-12-20
> **STREETURCHINE said:**
> right since i dont seem to be able to fix my xserver on hda1,
is there a way i can mount hda1 from my second hard drive and extract all my data as there are some documents on there i cant afford to loose i have dapper on hda1 and i am using edgy on the second hard drive..

                                   thanks

In your Edgy system, type

sudo mount /dev/hda1 /mnt

and all your stuff from hda1 is in /mnt

---

### Post by STREETURCHINE on 2006-12-20
In your Edgy system, type

sudo mount /dev/hda1 /mnt

and all your stuff from hda1 is in /mnt


ok now i have done this all my data is there now when i reinstall  dapper on hda1 will all this data be lost from hdb1(edgy)
if so how do i save it to edgy

---

### Post by aysiu on 2006-12-20
> **STREETURCHINE said:**
> In your Edgy system, type

sudo mount /dev/hda1 /mnt

and all your stuff from hda1 is in /mnt


ok now i have done this all my data is there now when i reinstall  dapper on hda1 will all this data be lost from hdb1(edgy)
if so how do i save it to edgy
You copy it from /mnt to some other place.

---

### Post by STREETURCHINE on 2006-12-20
thanks all for your help have copied all my stuff and have now reloaded dapper :D :D

---

