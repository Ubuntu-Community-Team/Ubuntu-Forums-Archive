---
title: "reinstalling ubuntu on a new partition (with screenshots)"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Tag_yer_dead on 2007-02-27
hey guys
just deleted my old ubuntu :( lol and am reinstalling it on a clean partition
I am a little confused on what to do next.....

I first created a new partition, used the ext3 filesystem
[[IMG]http://img178.imageshack.us/img178/9781/screenshot1ge7.th.png[/IMG]](http://img178.imageshack.us/my.php?image=screenshot1ge7.png)

so far all good....

but then i get to where id like to install ubuntu and i dont wanna make some mistake
I want Ubuntu installed on 12 Gb sda2 - so i selected that on everything
[[IMG]http://img176.imageshack.us/img176/2176/screenshot2mx3.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshot2mx3.png)

But i get the error "A partition is signed to more than one mount"
So where should i mount each thing - please be specific.

---

### Post by CSMatt on 2007-02-27
I don't think you can mount a single partition on more than one mount point at a time.

In any case, the mount point you want for the Ubuntu system partition is "/".  Since you didn't create a swap partition (you'll need a swap file in this case), you probably want the partition selection for "swap" to be blank.  The mount points for the other partitions should correspond to their partition designation ("/media/sda1" should be associated with sda1 and "/media/sdb1" should be associated with sdb2).  The partition designation is in the brackets of each partition's description in the list.

---

### Post by Kateikyoushi on 2007-02-28
You set one partition (the sda2) as swap, /, which can not be done.

Set the sdb2 to / and create a 1GB swap partition in the empty space and set the mount point as swap. 
If you want to mount the NTFS partition set it as /media/sda1 and untick the format option.

Here is a guide which might help. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

