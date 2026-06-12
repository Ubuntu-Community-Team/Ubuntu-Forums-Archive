---
title: "create new primary partition?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by frito on 2008-03-26
Is it possible to change a logical partition into a  primary partition?

currently my drive looks liek this

primary partition (20gb)
extended partition
 --->Storage (20GB)
 --->ubuntu  (20gb)
 --->pclinuxOS(20gb)

can i change one of these logicals into a primary partition or does this have to be done when you create your drive? (i know i will have to format it)

lets say i format PClinuxOS will i be able to put a primary partition after the extended partition?

---

### Post by herbster on 2008-03-26
IIRC, you can't change a logical to an extended. You can have up to 4 extended partitions under the "container."

---

### Post by housam on 2008-03-26
For a single HDD you can have only 4 primary partitions or 3 primary partitions and the forth will be an extended partition which can be divided to many logical partitions.( you can't change a logical one to a primary )

---

### Post by Bachstelze on 2008-03-26
> **frito said:**
> 
can i change one of these logicals into a primary partition or does this have to be done when you create your drive? (i know i will have to format it)

No. However, you can make a copy of it that will be primary with e.g. GParted (provided you have enough free space for it).

> **frito said:**
> lets say i format PClinuxOS will i be able to put a primary partition after the extended partition?

Yes. At worst, you'll have to shrink the Extended, which is just a matter of seconds.

---

