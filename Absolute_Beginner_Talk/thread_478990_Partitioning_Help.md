---
title: "Partitioning Help"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-19
Following [the guide on the Wiki]("https://help.ubuntu.com/community/HowtoPartition") (nice guide, if I may add :p) I'm stuck on a step.

*Select the partition that you want to resize. Click Enter.*

[http://img.zenixstudios.com/2007/6/20/png/s/Screenshot.png](http://img.zenixstudios.com/2007/6/20/png/s/Screenshot.png)

You see, on there I have the partition I want to resize highlighted.  I'd like to create a partition 20GBs (20,480MBs) for Ubuntu and save the other 100 for Windows.  When I hit 'Enter' (I'm assuming it means on my keyboard), nothing happens.

This is confusing me a lot, and yet again, I'm sure it's something obvious. :(

---

### Post by lamalex on 2007-06-19
looks like you have the *drive* selected, not the *partition*. select /dev/hdb1 instead of /dev/hdb

---

### Post by Rotaj on 2007-06-19
The first thing that sticks out is, where is your swap partition?
It should be twice as large as your ram, up to 1Gb.
You have not defined the usage of the space. You have just reserved it for future useage. Try right clicking on the 20 Gb partition( in Gparted) and see if any of the choices lead lead you foward with the wiki guide.

---

### Post by Hork on 2007-06-19
*looks like you have the drive selected, not the partition. select /dev/hdb1 instead of /dev/hdb*

Thanks, looks like that fixed it!

[I] 	The first thing that sticks out is, where is your swap partition?
It should be twice as large as your ram, up to 1Gb.
You have not defined the usage of the space. You have just reserved it for future useage. Try right clicking on the 20 Gb partition( in Gparted) and see if any of the choices lead lead you foward with the wiki guide.[/I]

Wait, this is confusing.  I just made a 60GB thing for Ubuntu and have 50GB of freespace.

I do make the file format ext3, right?

---

