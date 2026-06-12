---
title: "partitioning for ubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by striker4678 on 2007-06-20
Hey guys, a couple nights ago I made a huge mistake and accidentally deleted my windows whenever I installed ubunt feisty 
Since then I've used "Darik's boot and nuke" to delete any remaining files.
I tried using gpartedto set up a partition for ubuntu and one for windows, but honestly I didn't really know what I was doing.
I kind of forgot how I set up the windows partition, but I think it's just one big partition by itself.  I don't really know much about partitioning obviously...
but anyways tonight I'm going to install ubuntu, in the most user friendly way possible, how should I go about installing ubuntu without messing up anything with windows, how should I set up the patitioning? How exactly do I set up the partition? Which program should I use to set them up?

sorry i'm not the smartest computer user =p

---

### Post by finer recliner on 2007-06-20
for a dual boot system with windows xp and ubuntu do this:

3 partitions:
1st is formatted as NTFS for windows
2nd is formatted as ext3 for ubuntu
3rd is formatted as swap (ubuntu needs this)

your swap space should be about twice the size of your physical RAM
the rest of your harddrive can be split however you want between the ntfs and ext3. linux will not need as much as windows typically uses.

lastly: INSTALL WINDOWS FIRST!!

---

### Post by gdoermann on 2007-06-20
If you are going to use GRUB as a boot loader, I would add a /boot partition!  Every time you re-install windows you will have problems with GRUB, and it is MUCH easier to deal with if you have a separate partition for /boot.

---

### Post by hyper_ch on 2007-06-20
Hmmm, I'd got for a seperate /home partition... but I don't see why a seperrate /boot partition would help. I tend to think Windoze overwrites the masterboot record on the first booting harddisk anway... so why would a seperate /boot partition be of any use?

---

### Post by notbitmonk on 2007-06-20
I would consider a fourth partition to hols data files that might be shared between OS's unless you have a hard disk that serves the purpose.

---

### Post by hyper_ch on 2007-06-20
notbit: Installing the ext2/3 drivers in windows does the job :) or ntfs-3g in linux (however I'd go for the ext2/3 option)

---

### Post by shearn89 on 2007-06-20
just install windows, let it do its own partitioning, then before you've configured it and put loads of docs on it, install ubuntu (perhaps with a /home partition), and resize the 'doze partition during the install. worked for me...

---

### Post by Alex&amp;Linux on 2007-06-20
> **finer recliner said:**
> for a dual boot system with windows xp and ubuntu do this:

3 partitions:
1st is formatted as NTFS for windows
2nd is formatted as ext3 for ubuntu
3rd is formatted as swap (ubuntu needs this)

your swap space should be about twice the size of your physical RAM
the rest of your harddrive can be split however you want between the ntfs and ext3. linux will not need as much as windows typically uses.

lastly: INSTALL WINDOWS FIRST!!

Just wanted to agree with this, good plan.
To elaborate, its a great idea to start fresh when setting up a dual-boot, for stability reasons!
Great idea to install windows, and use a partitioning app to shrink your NTFS by the volume you want for your EXT2/3 + swap, then install Ubuntu using the "install on largest contigious [no idea how to spell that:)] space.
Everything will take care of its self after that point, clean and simple!

---

### Post by gdoermann on 2007-06-20
The reason it is good to have a boot partition is because if Windows bulldozes the GRUB with it's boot loader, then you can just activate the boot partition and it will again work.  From what I understand, if you activate a partition it looks at the first think on that partition to boot with; if you just have it included with your regular partition, than you have to reinstall the boot loader from the install disk if you ever have problems (this can be problematic... especially if you have Ubuntu on a separate drive).  But, it is very possible to restore GRUB if it is not on a different partition- I just like to reduce the work to do so.

---

### Post by hyper_ch on 2007-06-20
I didn't know that... and to be honest, I'm not entirely convinced that it works like that... I think the masterboot record is in the first partition on the first drive... hence if it's overwritten, it is overwritten... that's my thought of it...

---

