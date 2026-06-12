---
title: "2 partitions with same system"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-27
I run Kubuntu for personal computing. I find that often times i download stuff and clog my computer up with worthless things and find it easier to just reinstall the OS instead of weeding out the problems. If i wanted to partition only a small portion of the harddrive to a Kubuntu system that i would only use for non-fun reasons, how would i go about this?

---

### Post by ktown on 2007-06-27
Basically how do i partition Kubuntu two times on the same computer?

---

### Post by CheShA on 2007-06-27
Have you tried just putting in the kubuntu CD and re-running the installer? I think it shoudl give you the option to move your partitions ariound (i.e. shrink the partition you're currently using and then create a new partition in the space you have freed) then allow you to install to the new partition.  I would expect it to set up Grub automatcally to give you the option of booting into either/or. 

Most Linux distros can do this for an existing install of Windows - Kubuuntu should certainly be able to do it for another edition of kubuntu!

---

### Post by joe.turion64x2 on 2007-06-27
> **ktown said:**
> Basically how do i partition Kubuntu two times on the same computer?
It is a good practice to make a separate partition for your /home directory. During the install process check something like custom partitioning, there you can create a custom partition array. Doing a separate /home (you have to set the correct mount point) you will be able to reinstall as many times as you want (the / (root) partition only) while keeping your settings & files in /home (without formating) just be sure to use custom partitioning in every install so you do not format your whole drive.

---

### Post by ktown on 2007-06-27
alright i'll try save everything i really need before trying it and ill play around with the partitions. thanks guys (and maybe girls)

---

### Post by az on 2007-06-27
> **joe.turion64x2 said:**
> It is a good practice to make a separate partition for your /home directory. ... you will be able to reinstall as many times as you want (the / (root) partition only) while keeping your settings & files in /home (without formating) .

If you are playing around, you don't want to do that.  You can mess up your settings for your non-fun version of the application that way.

---

### Post by joe.turion64x2 on 2007-06-27
> **az said:**
> If you are playing around, you don't want to do that.  You can mess up your settings for your non-fun version of the application that way.
Not necessarily assuming you are reinstalling (install the same again). It is a better practice to hold a third partition for data, a partition to be mounted under the user's home directory. That way you can even dual boot Linuxes.

Edit: At least in Mandriva holding a /home partition and installing a newer version did not bother me at all, I have not tried with Ubuntu though.

---

