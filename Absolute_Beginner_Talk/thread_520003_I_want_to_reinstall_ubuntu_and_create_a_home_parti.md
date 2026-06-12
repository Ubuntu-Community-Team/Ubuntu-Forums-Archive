---
title: "I want to reinstall ubuntu and create a /home partition"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by GeneralHooHa on 2007-08-07
I messed up my ubuntu, and want to reinstall (I do not have too much data). I want to create a /home partition so that if this ever happens again I wont have any problems.

How exactally do I go about doing this? Could someone explain it carefully; I am a noob at the whole installation thing. I have an 88.9 gig hard drive with 1 gig of ram, and the Live CD right next to me.

Thank you very much!

---

### Post by jmnormand on 2007-08-07
pretty simple just go into manual partitioning.  as you make your partitions there is an options called mount.  create your partitions and set each as / (root), /home and swap.  there are others you can  make such as /boot but for a single boot system it should not real need anything else separated.

---

### Post by GeneralHooHa on 2007-08-07
Thank you. Could you please give me a reccommendation of how much space I should give to each? I don't really play games on this laptop, but I will do the occasional warcraft 3.

---

### Post by GeneralHooHa on 2007-08-07
Any recommendations?

---

### Post by bodhi.zazen on 2007-08-07
You can make 
/ = 5-10 Gb
swap = 1 Gb
/home = rest

It is not critical as you can resize the partitions later if you like.

---

