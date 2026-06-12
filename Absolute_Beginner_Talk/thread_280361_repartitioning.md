---
title: "repartitioning"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-19
i would like to know which program to install to be able to repartiotion my hard drive because i want to make a swap partition...as i didn't while installing kubuntu :D didn't know what to do with that :D

---

### Post by Sef on 2006-10-19
I would download and burn [GParted]("http://gparted.sourceforge.net/livecd.php") to create a swap.

How much ram do you have?  If you got at least a gigabyte of it, then likely you don't need to make a swap partition.

---

### Post by mendingo84 on 2006-10-19
Unfortunatelly, i only have 512MB o RAM. isn't there anything alike PartitionMagik?

---

### Post by CatKiller on 2006-10-19
GParted **is** like Partition Magic. Except it's Free.

---

### Post by mendingo84 on 2006-10-19
i read somewhere that this is a Gnome application...i'm using KDE but i'm guessing this is not an issue. am i right? i also saw that i am able to smoothly install gparted using Adept which makes me happy

---

### Post by CatKiller on 2006-10-19
It's probably not a good idea to be changing partitions that you're using to run the program to change the partitions.

Use a live cd. Either the GParted one, or the cd you installed from. Much safer.

---

### Post by ajgreeny on 2006-10-19
You certainly can use *gparted* in KDE, though it may need to install some other smaller packages of lib files etc as dependencies.  If you want to stick with KDE download and install *qtparted* instead; very similar but uses KDE lib files so you will probably already have all you need.

Sorry ignore that!  CatKiller is right, you shouldn't work on a mounted partition, ie, your kubuntu partition.  Get the live CD of Gparted instead.  It is terrific and always worth having around anyway.

---

### Post by bigken on 2006-10-19
Take Sefs advice use the [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD 
its very easy to use and reliable too ;)

---

