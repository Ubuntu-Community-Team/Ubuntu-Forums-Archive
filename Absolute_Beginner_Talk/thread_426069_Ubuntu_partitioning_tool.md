---
title: "Ubuntu partitioning tool"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-28
When I installed Ubuntu 6.10, I used the included partitioning application to create and size partitions on my master hard drive.  Now, I would like to increase the size of my XP partition (I only allowed 10 gb, and, although it deserves less space, XP is requiring more).

Can I use the 6.10 (or even the 7.04) partitioning software to resize the XP partion without destroying its functionality?

Thanks.

Caruso

---

### Post by raja on 2007-04-28
You can use the partitioner to resize NTFS partitions. However, the problem with trying to increase the size of the partition will  be that you may not have free space adjacent to it. 
Always have a backup of important data before any resizing  and if you are going to shrink it, be sure to defrag it thoroughly.

---

### Post by Sef on 2007-04-28
Yes, you can though I prefer to use [GParted]("http://gparted.sourceforge.net") to do partitioning since it is more up to date.

---

### Post by Najand on 2007-04-28
Sure you can. Gparted even have a seperate live CD you can download from their webpage too.... But be careful and backup all your important data.

---

### Post by laidback on 2007-04-28
Gparted Live is the best I've tried. The Live cd has a different version to the Ubuntu one, it'll also format memory sticks, I've never managed to get the Ubuntu version to do that.

---

### Post by Najand on 2007-04-28
The best thing about the live CD is that it can boot any partiotion on your harddisk... It is ideal when the stupid MS windows Bootloader write on MBR and you want to recover your grub.

---

### Post by carusoswi on 2007-04-28
> **Najand said:**
> The best thing about the live CD is that it can boot any partiotion on your harddisk... It is ideal when the stupid MS windows Bootloader write on MBR and you want to recover your grub.

Thanks for all the replies.  So, I downloaded the .iso file, burned a cd, booted it up.  I am presented with a screen listing the partitions on my drive with an option to highlight, then, either boot or edit.  I don't want to do either.  I would like to examine and resize the partitions.  I must be missing something.

Additional help, anyone?

Caruso

---

### Post by carusoswi on 2007-04-28
ok, so, I figured out that you have to select one of the lines at the top, press enter, and a view of my partitions shows on the screen.

However, before I can do anything, the program crashes and I get a black screen.

Obviously, I am still doing something wrong.

Help anyone?

Thanks.

Caruso

---

