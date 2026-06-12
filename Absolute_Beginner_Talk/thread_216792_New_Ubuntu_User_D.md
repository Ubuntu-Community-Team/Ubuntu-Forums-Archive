---
title: "New Ubuntu User :D"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Araelius on 2006-07-16
Just started my new installation for the first time and I must say that it was the most succesful Linux install without any issues. However, I must have mis-interpreted something while installing and accidentally reversed the partitions for my dual-boot. My intentions were to dedicate 60gb for Ubuntu and the remainder for WinXP, but I must have switched it by mistake.

Anyway, any tips on correcting this issue is greatly appreciated. Thank you in advance.

-Pablo(Araelius)

---

### Post by computx on 2006-07-16
So assuming you ended up with less space for ubuntu than you had planned. There are a number of partition resizers out there. From windows, partition magic 8 works well and understands ext3 partitions. From linux, a program like parted would work but must be run from a recovery cd as all partitions must not be mounted while resizing. I believe if you have an ubuntu live cd you could boot from it, pretend to install again and when you get to the partitions section you can resize then exit the install. 
I haven't tried this but I think it will work.
Maybe someone else will have a better solution. Bottom line it can be done.

---

### Post by Araelius on 2006-07-16
> **computx said:**
> So assuming you ended up with less space for ubuntu than you had planned. There are a number of partition resizers out there. From windows, partition magic 8 works well and understands ext3 partitions. From linux, a program like parted would work but must be run from a recovery cd as all partitions must not be mounted while resizing. I believe if you have an ubuntu live cd you could boot from it, pretend to install again and when you get to the partitions section you can resize then exit the install. 
I haven't tried this but I think it will work.
Maybe someone else will have a better solution. Bottom line it can be done.

Actually I should have been a little clearer, I ended up with more space than I planned :)

My main HD is 250gb and my secondary(used for storage) is a 40gb

Anyway I will give your suggestion a shot but any other imput from anyone would still be helpful.

---

