---
title: "Install on Powerbook G3 (Lombard)"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by rorykingms on 2006-08-23
Trying to install Dapper on a G3 Powerbook (Lombard), with the goal being a dual-boot machine. The machine will boot from the CD, and the installer will run, but when I get to the partition section something is amiss. I have already partitioned the 40 GB drive to 32 GB OS X (HFS+) and 5 GB (UFS) for Ubuntu, formatted using Disk Utility on OS X.

Choosing "Manually edit the partition table" lets me see the Ubuntu partition, but there is a yellow triangle near it and the file system is listed as unknown. If I click Forward, the next screen allows me to choose which partition to use (Prepare mount points). Here I have tried to place all the mount points on the ubuntu partition and checking the Reformat box; after completing all the mount points, the Forward button remains greyed out, halting the installation. Trying to put the swap drive on the OS X partition as an experiment has no results.

My questions at this point:

Which option do I choose for "Prepare disk space" to create a dual-boot machine: Erase entire disk, Use the largest continuous free space, or Manually edit the partition table?

If I edit the partition table, what are the steps (if any) to prepare the ubuntu partition to be recognized by the installer?

Is there some other reason the installer's Forward button is greyed out?

Is there an easier/better way to create a dual-boot Mac/Ubuntu machine?

---

### Post by timbobsteve on 2006-08-23
When you choose to manually edit the partition table you have to re-format (or at least change) the filesystem type of the new partition. 

When it says "unknown partition type" that means that it will not try to install or assign a mount point to it. Go back one step, select the partition and change it to an ext3 partition, then format it in the next step. That should give you a working ext3 partition for the Ubuntu installer to use. Simply assigning the space does not mean Ubuntu knows what to do with it ;)

I hope I understood your question correctly. Good luck with this. Do let us know how you go with it as I too am going to be putting (X)Ubuntu on my G3 ibook.

Have fun.

---

### Post by iamhugeinjapan on 2006-08-23
I have run Ubuntu Hoary and Dapper on my Lombard. By far the fastest experience I've had has been with Xubuntu Dapper.

Hopefully you can get your dual boot going ok, don't give up, it will run flawlessly once it boots!

---

### Post by rorykingms on 2006-08-24
> When you choose to manually edit the partition table you have to re-format (or at least change) the filesystem type of the new partition. 

When it says "unknown partition type" that means that it will not try to install or assign a mount point to it. Go back one step, select the partition and change it to an ext3 partition, then format it in the next step. That should give you a working ext3 partition for the Ubuntu installer to use. Simply assigning the space does not mean Ubuntu knows what to do with it.


That I understand. Here's what I tried with no success:

Manually partition > Highlight desired ubuntu partition > F12 to select "New" > Choose ext3 as the filesystem type (leaving everything else as is). At this point the partitioning job shows up in the to-do list, and clicking the Forward button seems to execute the partition request. The next screen asks where the mount points should go, and after setting them all to the correct partition, the Forward button is still greyed out.

Now for the really bizarre part: clicking Back in the installer takes me back to the partitions screen, and the ubuntu partition shows up as an unknown filesystem. Shouldn't it show up as ext3? Is the installer just not able to format the hard drive?

---

### Post by iamhugeinjapan on 2006-08-24
Can you use GParted in the livecd GNOME Systems menu to edit the partitions first?  The partitioner in the install sequence is known to be a bit flakey.

---

### Post by rorykingms on 2006-08-24
> **iamhugeinjapan said:**
> Can you use GParted in the livecd GNOME Systems menu to edit the partitions first?  The partitioner in the install sequence is known to be a bit flakey.

Yep, that worked. I guess there was some issue with the installer's partitioner. After several tries, here's what (seemed) to work (and what I recommend):

If you've already made your partition in OS X,  and the installer does not let you change the file format, you need to open the Gnome Partition app, select the partition, then F12 (or go to the Partition menu) > Filesystem > ext3. Then click the green check to start the process.

Now run the installer. When you get to the disk screen, you should find that the partition is now recognized as a valid installation point. It might offer to erase the partition and resize it if a previous install crashed part-way through. :) Go ahead and select the ext3 partition. The install should proceed accordingly.

(Unless you really know what you're doing, I personally do not recommend selecting "Manually edit the partition table." I made a swap partition in an effort to figure everything out; not sure if that was really necessary or not. I also received an error message about not finding a NewWorld partition; this was the first time the installer mentioned anything about this. So really, avoid manually editing the partition in the installer unless you are more experienced than I am.)

Well, it's up and running! And thanks for the tip about Xubuntu, which is what I installed. Kinda' snappy on this ol' machine!

---

