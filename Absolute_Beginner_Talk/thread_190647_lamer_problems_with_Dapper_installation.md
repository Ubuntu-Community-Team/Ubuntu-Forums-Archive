---
title: "lamer problems with Dapper installation"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Tibor60 on 2006-06-06
I am confused with the installation. I had a 40 GB hard disk, and there is a partition with 7 GB, no files on it, formatted with an ext3 filesystem. I would like to install the Dappper on this partition, without any modification of partitions on the drive. But the installer give no option for that, it wants all the time resize, format, free space etc., but not simply the option where I can say that the system should be installed on hdx2. I do not want to do any partitioning... 

How to solve this problem?

---

### Post by steve.horsley on 2006-06-06
You must use custom partitioning for this. You must also create a swap partition, I suggest 1Gig would do nicely but you could get away with 500M. Other than that, don't resize anything in the partitioner. Then after the partitioner finishes, you can specify that 7-gig partition should be mounted as /, leaving the other partitions with the suggested mount points. It's a bit daffy about what it suggests to format, so don't worry about correcting that.

If you have other data on the disk, make a backup first.

Good luck.

---

### Post by Tibor60 on 2006-06-06
It was impossible to do that. Even if I choose at preparing the HD right, when going to preparing mount points, there is seen only my other HD, where I would not like to install anything. Why is it so, the partition I want ti install is on the boot HD...?

---

### Post by steve.horsley on 2006-06-06
Can I suggest that you download the text-mode installer CD rather than the live CD then? I have to admit, I don't trust the live CD installer, and your story only reinforces that feeling.

---

### Post by aysiu on 2006-06-06
Which of these three screens are you *not* getting?

---

### Post by Tibor60 on 2006-06-07
I see all these screens, but on the first (prepare mount points) I see only one HD, and I do not want to install here anything. On the other 2 screens I see both hard drives...

---

### Post by Tibor60 on 2006-06-07
Steve, the text mode CD is with the name of "alternate"?

---

### Post by Tibor60 on 2006-06-07
It seems that Dapper does not like my system. The installing process went without error from the text install CD, but the system can not boot. The booting process starts, but stalles at the second row... 

Mounting the root file system
Waiting the root file system

and here is the end. No error messages, simple stalling. and I can go out from this only turning out the PC.

---

### Post by steve.horsley on 2006-06-07
Bummer. I don't know what to say about that, except maybe try a different distro. Try downloading the Knoppix live CD, and see what that does.

What is the  output from the Ubuntu live CD when you enter the command: > sudo fdisk -l?

---

### Post by Tibor60 on 2006-06-07
Thanks for the idea, fdisk -l was showing me the problem.
Yes, it is a bit bumpy... but the solution is found. My old system finds the HD as hdd5, and the Dapper text installer find it also on hdd5. So fstab is done for hdd5.
But the live CD, and the installed version of Dapper count this HD on hdh5. So the text installer did the fstab as hdd5, but the installed system at booting count it on hdh5... and so can not find anything. And all the CD drive, DVD drive, other hard drive was counted with bad device names. I corrected the fstab and now the system is booting well.
But, to tell the truth, I am a bit confused with this. Ubuntu 5.05, Knoppix Live CD, Rescue CD, tomsrbt all place the device names in the same way. Why ubuntu 6.06 does it in a different, complicated way?

---

