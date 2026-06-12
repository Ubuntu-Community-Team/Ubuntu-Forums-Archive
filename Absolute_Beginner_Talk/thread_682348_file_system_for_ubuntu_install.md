---
title: "file system for ubuntu install"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by corkscrew on 2008-01-29
Hi,
I'm complete newbie to ubuntu. I wish to install it on my laptop as a dual boot with winxp pro. The HD is currently split in 3, 1 hidden restore partition, c: 40 gig where xp is and 100 gig D: drive for data. Both are NTFS.
What would be the best set up for an ubuntu install?
I have read somwhere ubuntu wont run on ntfs is that true?

---

### Post by c0mp13371331337 on 2008-01-29
Very true, NTFS will not work.  You'll want to use ext3, and I'd recommend setting a separate partition for your /home folder, so if you need/want to reinstall Ubuntu, you can keep all your files and settings, just reinstall the / (root) partition.

Oh, and welcome to the community!

---

### Post by jaytek13 on 2008-01-29
No, Ubuntu or any Linux distribution won't "run" on NTFS. The default filesystem is ext3 which is considered the best Linux filesystem by most, such as it is the default for almost every distribution.

Anyways, you will be able to read your NTFS partition in Ubuntu regardless of the filesystem that Linux is using. There are also some windows tools that allow you to read ext3 filesystems from within windows.

---

### Post by iansane on 2008-01-29
Right. Ubuntu doesn't run on ntfs. It's ext3 and the live cd has a partition editor. Use it to reformat the partition or delete it and when install gets to that point, tell it to use the largest contiguos free space and it will format for you. Actually I think you can just run the cd and tell it which partition to use.

---

### Post by Mze on 2008-01-29
Download the [Gparted CD]("http://gparted.sourceforge.net/") and resize your 100 gig drive. 10 gig or more if you want. Format it to ext3. 

Grab the Ubuntu live CD, test it out to see if it works with your laptop. Install Ubuntu to the ext3 partition you've already created. Ubuntu should create it's own swap partition within the ext3 partition.

You may want to read up on dual-boot scenarios before going ahead.

Don't forget to back up your data. Defragment your WinXP drive prior to partitioning and Ubuntu install. Shut WinXP down properly before going ahead with your Ubuntu install.

further [reading]("http://www.apcstart.com/node/5162/") recommended

---

### Post by corkscrew on 2008-01-29
Hi 
thanks, never thought of using part of the 100 gig drive for ext3, you say ubuntu will automatically create swap partition, all the stuff i've read says you have to create it and to make it 512mb. Will i be able to read my data on the ntfs drives?

---

### Post by corkscrew on 2008-01-29
thanks for your help
do you mean once i creat ext3 partition i need to split that into 3, 1 for swap, 1 for home and 1 for the root?

---

### Post by jaytek13 on 2008-01-29
> **corkscrew said:**
> Hi 
thanks, never thought of using part of the 100 gig drive for ext3, you say ubuntu will automatically create swap partition, all the stuff i've read says you have to create it and to make it 512mb. Will i be able to read my data on the ntfs drives?

Oh, no. You won't have to do any of this. You have the option to, but manually editing the partition for Linux yourself is relegated to the "advanced' Linux distributions and how things used to be 7 years ago. There is no longer a need to specifically specify the partitions, the installer will do it for you.

---

### Post by oedha on 2008-01-29
yup...just get gparted and focus to your 100gb partition
resize it to 80 or 90 and keep it NTFS
on the new partition....create new partition as ext3
btw...what is your RAM...if you have more than 1GB...you dont have to make swap partition

then install ubuntu from ubuntu live cd

after finished....dont forget to install NTFS configuration Tool to give you full akses to your NTFS partitions.....
so you can use your data both for win and lin.....

regards;
~E~

---

### Post by corkscrew on 2008-01-30
thanks for your help, I have 2 gig of ram installed,jaytek13 says all the partitions are created automatically when you install, will it see the 2 gig and not make a swap partition?

---

### Post by Aurora@FleetBuzz on 2008-01-30
Here is a link to the videos that I used as a reference the first time I messed around with Gparted.  
[http://www.linux.com/articles/114157](http://www.linux.com/articles/114157)

---

