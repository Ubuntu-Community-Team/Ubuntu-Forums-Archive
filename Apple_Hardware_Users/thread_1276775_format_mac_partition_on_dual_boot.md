---
title: "format mac partition on dual boot"
date: 2009-09-27
forum: Apple Hardware Users
---

### Post by inphektion on 2009-09-27
It seems to get snow leopard installed I'll need to format my mac partition and re-do it.  I don't have anything on there I care about except i do use refit.  I do not want to lose my ability to boot into my ubuntu that is booted from a separate /boot ext3 partition.  
Once i format the mac partition will this cause issues since refit might then be gone?  I can alway put refit back of course once snow leopard is there.

---

### Post by Bachstelze on 2009-09-27
> **inphektion said:**
> I can alway put refit back of course once snow leopard is there.

That will work... if you don't have to reformat your whole drive in the process (that's what I had to do, apparently because I had more then 4 partitions on it).

---

### Post by inphektion on 2009-09-28
wait why would i have to reformat my whole drive?  will the disk utility tell me I can't reformat that partition?  No way I'm willing to reformat my ubuntu partitions.  I have a mac hfs partition, /boot ext3, / ext4, /home ext4, and swap.  5 partitions total.

---

### Post by gwydionwaters on 2009-09-28
Just use gparted and format the the partition

---

