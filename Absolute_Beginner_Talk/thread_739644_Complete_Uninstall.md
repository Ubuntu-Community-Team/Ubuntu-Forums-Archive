---
title: "Complete Uninstall?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by New2Linux0319 on 2008-03-29
hi,
i want to completely remove all Linux from my computer and revert it back to free space.
how can i do this?

i plan to reinstall from the beginning.  i have no saved files to worry about.  trying to become more familiar with the process. 

thanks,

---

### Post by scragar on 2008-03-29
it would proberly be easier to just use the liveCD and gparted(System > Administration > Partition Editor) to remove the ubuntu and swap partitions, then assign them to whatever other partition you want, or leave it as free space if your planning to install something else(since it will normaly want to format and partition itself)

---

### Post by spiderbatdad on 2008-03-29
Generally, you run the installation cd and have it rewrite the disk.
Running sudo rm -rf is supposed to delete your file system. I can't imagine it gets very far, though, before the system crashes.

---

### Post by Lvcoyote on 2008-03-29
You can use a utility called "Kill Disk" to wipe the drive clean as it was when bought new.

---

### Post by scragar on 2008-03-29
it's ```
sudo rm -rf /
``` It get's very far actualy, since linux doesn't lock files it on falls on programs that use virtual files and when it starts attempting to do funny things to /dev
[http://hohle.net/scrap_post.php?post=23](http://hohle.net/scrap_post.php?post=23)

in order to completely remove the system it's important to unmount / first, which cannot be done while the system is running. Which is why the live CD will be needed to clean of it's last few files

---

### Post by Catalyst2Death on 2008-03-29
when you boot into the live cd (which I'm assuming you have, because its what I'm familiar with) you will reach a point when it will ask you how you want to format the disks.  It is not necessary to wipe the disk clean, and then install.  You can tell the installer to wipe the disks for you.  If you choose manual you can edit the partitions.  There are many different programs which can resize your disk, If you installing from the terminal you can use cfdisk.  I am not familiar with this program, so I'll describe how to do it with the ubuntu install  Generally, here is how ubuntu partitions your hard drive:

First it has a swap, this behaves like virtual ram, generally you should have a swap 2X the physical ram in the machine.  Next you have your the system partition, it is what the operating system will install onto.  You can chose from multiple filesystems, but generally ext3 will be the best for most jobs.

Here is how the process would go:

Select a partition and select the "delete partition" button, it will the show free space where your partition used to exist.  Repeat this process until you only have free space (only if you want to wipe the entire disk!)

Now we create the swap partition
Next select the "create partition" button.  This will open up a window which will have different options.  Under the file system drop down list, select swap.  There is another option for how large you want to make the partition in Mb, (by default it will make it as large as the space available) enter 2x the amount of ram you have installed.  (if you have more than 1 gb of ram, then you don't have to follow the 2x rule, instead you can decide how much you want to allocate to swap) Click OK

Next we create the primary partition, you can do this by selecting create partition, and then selecting ext3 as the file system.  Then under mount point set it to "/" click ok

you should be set! if you want a more detailed explanation about partitioning you can check here:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

