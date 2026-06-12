---
title: "Partitioning"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Hi_Im_Fubar on 2006-07-04
I've tried searching but I couldn't find a thread that helps me. So I'll post my question here. (Sorry if there are anoter million threads with the same question but I can't find it) Okay, now to my question:

Do I need to partition my drive BEFORE installing ubuntu? I have one drive and two partitions so far. C: and D: C is my main windows drive and D is my backup drive (was there since I installed windows). Also, do you have any specific step by step guide to partitioning? Thank you.

---

### Post by Jagot on 2006-07-04
You don't need to partition before the install.  The graphical install on the Desktop (live) CD is straight forward, and you can see the process of setting up a dual boot including the partition stage on (my personal favourite) the Alternate Install CD:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Hi_Im_Fubar on 2006-07-04
I forgot to ask: IS there a way to make a single drive that both windows AND ubuntu share? So I can keep all my data on that drive?

---

### Post by Jagot on 2006-07-04
Yep - the tutorial I posted shows you the installation of Ubuntu on the same drive as Windows.

---

### Post by crystal on 2006-07-04
> I forgot to ask: IS there a way to make a single drive that both windows AND ubuntu share? So I can keep all my data on that drive?
Take a look at this [Partitioning Windows and Ubuntu](http://psychocats.net/ubuntu/partitioning.html) tutorial. I went for the NTFS + Ext3 configuration, and it worked well.

---

### Post by Hi_Im_Fubar on 2006-07-04
Thanks. You guys are really fast! But does the installer help me make the fat32 partition too?

---

### Post by Jagot on 2006-07-04
The one in the graphical install certainly allows you to create a FAT32 partition and I'm fairly sure the text install does as well.

---

### Post by bruenig on 2006-07-04
in the graphical install, you will get to a place where it asks you to partition, if you want data sharing between the two, I recommend selecting manually partition the partition table.
Once there do the following:

1. Resize the windows partition or C drive.

2. Do what you want with the D drive, if it is just backup I would just delete it as that implies you have all of that data elsewhere.

3.Create a /root partition, this will be your ubuntu partition, make sure you format the filesystem as ext3 and when it asks you where to mount it after you have partitioned everything, select /

4.Create a swap partition which should be twice the size of your RAM and format it as linux-swap. When it asks you where to mount it after you have partitioned everything, select swap

5.create an extra partition and format it as fat32, this will be your data sharing, accept the default mount point probably looks something like this /media/sda4, on this partition you can put all of your backup D stuff if you chose to delete it.

---

