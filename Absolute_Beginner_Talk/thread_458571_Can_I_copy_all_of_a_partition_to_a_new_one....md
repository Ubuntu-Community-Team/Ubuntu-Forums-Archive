---
title: "Can I copy all of a partition to a new one..."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-29
So, I wanted to restore my old 20gb Ubuntu partition (only 2gb used) to a new 8gb partition, but partimage wont do it.

I want to restore my 20gb Ubuntu to a 20gb external drive, then just copy all the files, while on the LiveCD, to my new partition.

Can this be done?

Removable partition is sdc1, partition I want all the info on is sda2.

---

### Post by Clay_Banger on 2007-05-29
have you tried using gparted to resize, copy, then move the partitions around?

ie. for the 20gb --> 8gb:
resize it down to less then 8, copy it to where you want it, then check for errors & that all the data is there, then delete the original 20

---

### Post by gohanssjn on 2007-05-30
Well, here's the weird thing now :(

My install is only like 3gb large, but when I restore it using partimage it shows 12gb and won't resize smaller than that.  I'm locked at 12gb for some reason.  And I know it's not really that large, my .000 file is only 804mb in size :(

---

### Post by gohanssjn on 2007-05-30
Well, I hope we can find something in the next 8 hours, or when I get home, I'm just going to have to do a clean install to that 8gb partition.

---

### Post by gohanssjn on 2007-05-30
One more bump, I pray for an idea :(

---

