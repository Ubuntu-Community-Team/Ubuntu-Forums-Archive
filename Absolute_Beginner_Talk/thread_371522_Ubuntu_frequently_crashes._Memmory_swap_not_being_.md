---
title: "Ubuntu frequently crashes. Memmory swap not being used."
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Charco on 2007-02-27
My system crashes with more than 3 programs running. I don't think my system is using the swap partion (512 MB) for some reason. I look at the system monitor and it's always at 0%, 0 bytes. How do I activate this?

---

### Post by Kateikyoushi on 2007-02-27
What is the output of free -l ?

---

### Post by Charco on 2007-02-27
total       used       free     shared    buffers     cached
Mem:        450904     437468      13436          0       5628     125680
Low:        450904     437468      13436
High:            0          0          0
-/+ buffers/cache:     306160     144744
Swap:            0          0          0

[[IMG]http://img99.imageshack.us/img99/5397/memoryay1.th.png[/IMG]](http://img99.imageshack.us/my.php?image=memoryay1.png)

---

### Post by bodhi.zazen on 2007-02-27
Activate swap with :

swapon /dev/hdxy

Where /dev/hdxy is your swap partition.

Also add an entry to fstab :

> /dev/hdxy  swap  swap  defaults  0  0

---

### Post by Charco on 2007-02-27
Thanks so much! You people are amazing!

---

