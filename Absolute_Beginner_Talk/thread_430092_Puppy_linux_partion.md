---
title: "Puppy linux partion"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-01
I cant install puppy linux on my new partion dev/sda 2

Heres a pic 
[http://img170.imageshack.us/img170/351/iownyoubl7.png](http://img170.imageshack.us/img170/351/iownyoubl7.png)

Puppy doesnt seem to detect it!

---

### Post by mojo123 on 2007-05-01
please help!

---

### Post by louieb on 2007-05-01
Thats because sda2 is an extended partition.  An extended partition contains other partitions not data. You need a primary or logical partition to hold data.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by confused57 on 2007-05-01
louieb's right, you'll need to create a logical partition within the extended partition or create another primary partition.  The one time I installed Puppy, I had to create and format an ext2 partition before trying to install Puppy.  I didn't really find the installed Puppy any faster than the live cd, which enables you to create a persistent image(DotPup, I think it's called) on your hard drive.  The newest version of Puppy may be different, this was nearly a year ago that I installed it.

---

### Post by mojo123 on 2007-05-01
omfg thank you!!!!!! One question i installed puppy on sda 6 how can i add this to grub?

---

### Post by confused57 on 2007-05-01
> **mojo123 said:**
> omfg thank you!!!!!! One question i installed puppy on sda 6 how can i add this to grub?
See this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

the configfile method should work.

---

