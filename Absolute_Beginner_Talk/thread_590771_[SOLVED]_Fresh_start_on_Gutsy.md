---
title: "[SOLVED] Fresh start on Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by marbig on 2007-10-25
Totally stuffed up an upgrade Fiesty to Gutsy. So decided to uninstall altogether and start anew following instructions I found in another forum.
> Back up any of your files that you want that are on the Linux partitions and:

Boot to the recovery console using your XP CDROM, enter the commands "fixboot" then "fixmbr" and reboot. XP should boot, GRUB will not load at all as it should have been removed from the bootloader.

Once XP has booted go to start -> run and enter "diskmgmt.msc". Look for the Linux partitions and delete and format them into NTFS or FAT32. If you're not sure which are the Linux partitions post up what you can see in the list before proceeding.
This was posted over a year ago so I don't think he might see my posting. I'm at the stage of looking at the partitions and I don't know which are the linux ones. This [LINK]("http://img.photobucket.com/albums/v61/marbig/partitions.jpg") will take you to a jpg of what I am looking at in the disk management program.
Can anyone please tell me what to delete?

---

### Post by Sef on 2007-10-25
1) You are (want to) dual booting XP and Gustsy.

2) Just install Gutsy on its partition, and you should be able to boot up XP too.

3) If you can't then let us know and we will help you further.

---

### Post by Afkpuz on 2007-10-25
It looks like you have a whole bunch of partitions on you first hard drive and then some back up on your second hard drive.  I'm not sure how it would work with a live CD, but I can tell you how it would work with the alternate install disc.  

If you use the alternate install disc:
Start the fresh install.  Once you get to the partitioner, DON"T DELETE THE NFTS partitions.    Those are your windows partitions.  It looks like you have about 90 GBs you can free up on your first drive.  So, the 84.4 Gb and 2.90 gb partitions are the ones you can format, as well as the random 439MB partition on the end.  So, delete all those partitions in the partition manager, then use the "guided-use largest continuous free space" option.  It will set it up for you  and set up your swap area too.  

Then, much later in the install process, it will prompt you to install Grub to the master boot loader, or something like that.  Say "no".  It will then ask you where to install the boot loader.  If you used the guided partitioning, you want to install it to the 2nd partition of your first hard drive.  that is (hd0,1)  or (first hard drive,2nd partition)

So heres the short version.

1.) Windows should be installed before you install linux and it should be on the first partition of the hard drive

2.) Linux can then sit on the 2nd half of the hard drive.  Don't forget to partition a swap area

3.) Install the grub loader to the partition that linux sits on.  usually (hd0,1)

Then you should be able to dual boot

---

### Post by marbig on 2007-10-25
Thanks Afkpuz [and Sef]. Busy now and will return later to follow your advice. Just one question Afkpuz. What is the "alternate install disk"? How is it different from the live cd?
I'll post later to report on how I went.

---

### Post by marbig on 2007-10-25
> What is the "alternate install disk"? How is it different from the live cd?
Found the difference. Downloading it now. :)

---

