---
title: "removing fedora core 6"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by adityak_28 on 2007-01-19
hi all,
  i'm a total newbie to linux so pls excuse any stupid questions, i'll try to learn fast. i have fedora core 6 installed on my system now and i wish to change to ubuntu cos of the beautiful community and n00b friendliness. also sometimes the x server doesn't start up in fedora and sometimes the mouse pointer is missing! i had  the mouse pointer problem in fedora core 5 too. anyway my friend gave me the ubuntu 6.06 cd and i wish to install it on my system. how do i remove fedora from my system without losing my xp installation? those of you who have had experience with fedora might also know of LVM that it creates during install. what is LVM and will i be able to remove it? also all the partition programs that i have give some error reading the LVM. why is this so and what should be done to remove fedora and install ubuntu?

  all help will be greatly appreciated and i hope to have a complete linux experience with ubuntu. thnx.

---

### Post by bluefrog on 2007-01-19
just install on top of FC6.

regarding LVM and partitioning: either you will use the LVM groups/volumes or you will tell ubuntu to use the entire disk (so it will erase everything).

If you are totally new to OS install (windows, linux or whatever) this might be the easiest.

otherwise you can also choose the manual partitioner and create:

/           10 GB   (yes overkill, but I am not interested in endless/useless fight with the size of actual HDD)
swap     500 MB
/home   the rest of your HDD

James

---

### Post by adityak_28 on 2007-01-19
thanks for the speedy reply! is there an ideal size for swap? most of the sites say that it should be 1.5 times the ram. also what is the use of creating /boot (~100mb)?

---

### Post by bluefrog on 2007-01-19
swap is needeed when you have low RAM.

with 512 RAM the euqivalent in swap should be ebough. you can make it higher if you wish. no problem.

/boot is needed if you use LVM and stick / inside the LVM.

James

---

### Post by adityak_28 on 2007-01-19
thanks james! now i must go and try to install ubuntu. my first cup of ubuntu! cheers!

---

