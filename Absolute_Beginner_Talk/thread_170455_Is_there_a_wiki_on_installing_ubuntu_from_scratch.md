---
title: "Is there a wiki on installing ubuntu from scratch"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by the_tiger on 2006-05-04
Title is pretty self explanatory. Simple googling and searching in the forum did not bring up it up quickly for me. Surely this sort of thing should be easily accessible to make beginners lifes easier?

---

### Post by manicka on 2006-05-04
there's a nice page on dual booting here

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by manicka on 2006-05-04
Once up and running you'll find this a handy reference

[http://doc.gwos.org/index.php/BreezyStarterGuide](http://doc.gwos.org/index.php/BreezyStarterGuide)

---

### Post by the_tiger on 2006-05-04
I still haven't seen anywhere that gives a comprehensive summary of root and home partitions, swap and which file system to use ext2/ext3

---

### Post by muep on 2006-05-04
If you don't know you want to do otherwise, select ext3 as the filesystem. It is the default and it works reliably.



For partitioning, it depends a bit. 
One of the most convenient partiotion setups is this, 3 partiotions total:
-Swap, the amount of this varies, but 2 times the amount of your RAM is a good guess. No more than 1 GB though, on most situations.

-The root partition. 10 GB should be enough. The basic install consumes about 2GB. If you know you will need more, then make the root partition bigger.

-the rest space for the home partition.

---

### Post by manicka on 2006-05-04
I think the_tiger knows what to do, but is wondering why there isn't more info out there for beginners.

---

### Post by the_tiger on 2006-05-04
spot on manicka!:cool:

---

