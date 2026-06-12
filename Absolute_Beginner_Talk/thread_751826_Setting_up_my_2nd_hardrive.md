---
title: "Setting up my 2nd hardrive"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by astro4travel on 2008-04-10
I have Ubuntu 7.10 presently installed on my second hard drive. I run windows XP on my first one. On drive F, or the second hard drive, I also have some storage files from XP on there. Now, what I would like to do is this. When the next version of Ubuntu comes out (Heron), I would like to do a clean reinstall. I would like to set it up on the F:/ drive so that I can have a separate partition for the / or home folder. This way when I decide to upgrade next time around, I will have all of my past settings. I'm a little new to partitioning and I do have G-parted on a disk if that would help.. I just have to know how to go about it to make good use of rest of F:/ drive. I would also like to leave the Windows files that are on F:/ drive untouched.F:/ drive has 250 megabytes of space. Could someone possibly walk me through it? Thanks in advance. Michael

---

### Post by oliviacond on 2008-04-11
you can do a clean reinstall by running the heron live cd and install in your gutsy partition. if you want to have all of your past setting, then you can just upgrade to heron with update manager.

---

### Post by mick8985 on 2008-04-11
So you want to partition the disk to have a small amount of storage in ntfs for your windows files?
Boot up the disk with gparted on, select your disk, select the ntfs partition which is taking up all the current space, and click resize/move, drag little graphical representation until its the desired size and click accept. Now you will have your ntfs partition and some unallocated space, click accept. now when you load the livecd you can just make ubuntu take up that unallocated space you left.

---

