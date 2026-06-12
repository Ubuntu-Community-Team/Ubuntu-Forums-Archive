---
title: "Partition attempting to write to my c drive"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-05
Hi,

I am trying to install dapper drake and in fact writing this from the live CD.

I have created the partitions and am in the prepare mounts page. I have selected the root, swap, and home mounts. I am trying to install to a second drive and that is where I created my partitions except for a 10 gig area for my windows docs.

My problem is that linux wants to mount something on my 'c' drive which is where I have windows xp.

The choices it gives me are:
 Blank,  /media,  /,  /home, /boot, /usr, and /var.

I have tried to change to the second drive but it will not let me.

Oh yes. I will be trying to do a dual boot.

Thank you,
Carolyn

---

### Post by bulldog on 2006-11-05
It won't mount anything **on** your c:\ drive.

It will probably mount your c:\ drive in the /media folder so you can access it from Ubuntu.

Look carefully you don't set your windows partition to be formatted.

---

### Post by Carolyn62 on 2006-11-05
Thank you,

Seems it did not like the way I did my partitions as it refused to accept one of them.

I tried to set up 3 of them:
/ 10 gig
/swap 768mb
/home balance of my 40 gig hard drive.

and the one for home turned black and won't partition so back to square one. I had them all set up as primaries with root and home as ext 3.

Carolyn

---

### Post by bulldog on 2006-11-05
Download the gparted live cd and do your partitioning by booting from the cd.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This is much more easy as using the live cd.

---

