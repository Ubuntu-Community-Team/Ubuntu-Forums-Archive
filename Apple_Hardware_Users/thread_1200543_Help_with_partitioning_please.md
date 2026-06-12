---
title: "Help with partitioning please?"
date: 2009-06-30
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-06-30
I am very new to ubuntu 9.04 (been a long standing Mac OS X user) and have a couple of questions/issues re partitioning and mounting file systems.

I currently have the following setup:
/dev/sda1 fat32 EFI
/dev/sda2 hfs+ Macintosh HD
/dev/sda3 linux+swap
/dev/sda4 ext3 /boot

/dev/sde1 fat31 EFI
/dev/sde2 ext3 /
/dev/sde3 ext3 /usr
/dev/sde4 ext3 /home

I am currently using simple backup to backup up to /var/backup...so I thought installing a separate external disk, partitioning it, and setting up a file system for the destination for simple backup would be a better solution than backing up to the same physical disk.

So I ran gparted and created two new ext3 partitions on the new external drive...BUT...how can I create a filesystem on the new partition that I can use for backups...no partition mount option is available????

So how do I go about mounting a partition on the new disk and get it incorporated as part of the file system?

OR....

Do I have to move part of / that is on /dev/sde2 to the new partition and if so how do I go about that?

Hope you can help please!

---

### Post by Richardcavell on 2009-06-30
Firstly, I think you should clarify what you are trying to do.

If your objective is to have an easy backup solution, then my suggestion is to format the external drive as one big file system. Then use rsync or some other backup software to copy your existing file system to the backup external drive. The fact that your existing file system is spread across multiple partitions and drives will make no difference to a file-for-file clone.

I think what you're trying to do is to mount the external backup drive as /var/backup. You can do this as follows:

mkdir /var/backup (if you haven't already)
df -h
(Now figure out which one is your hard disk. It might be, say, /dev/hd2)
sudo mount /dev/hd2 /var/backup (or replace hd2 with whatever your external drive is within /dev)

Now you backup up your whole file system except for /var/backup itself into /var/backup, and you have cloned your whole file system onto your second external hard disk. You can then

umount /var/backup

But I prefer the first option.

Richard

---

### Post by EvansFive on 2009-07-01
What I have done is partition the external disk into two partitions:
1) Simple Backup "hourly" incremental backups - I have reasonably replicated Time Machine as much as possible.  So I can recover file(s)/folder(s) from a point back in time.  That is all working nicely!
2) A separate partition for rsync backup as you suggested, where I can clone the entire file system on say a weekly basis or when major changes have occurred.

There are a number of other volumes (for Mac OS X use) that get mounted at /media at boot time by Ubuntu, I don't want to backup these up because they are backed up via Mac OS X. So I have crafted the following rsync command:

sudo rsync -av --progress --delete -log-file=.... \
      --exclude=/media   /    /media/FrodoFullBackup

So what I am "hoping" is that this will copy the entire root "/" filesystem to the external drive mounted at /media/FrodoFullBackup BUT not include other external volumes that are mounted at /media!

Have I got it about right or does this need some more tweaking?  Any assistance would be appreciated given my lack of familiarity with Ubuntu.

Thanks
Peter

---

### Post by Richardcavell on 2009-07-01
I have an idea. Instead of delving into man rsync, take a look at grsync. It's what I use. It's a graphical frontend to rsync (much as Carbon Copy Cloner is an rsync front end for OS X). I find graphical user interfaces less screwupable than bash commands.

Richard

---

### Post by EvansFive on 2009-07-02
Ok I have had a look at grsync and I agree much less risk than using bash!

Sorry for my ignorance but I am still a little confused over how to correctly specify the source and destination paths.

Firstly I assume I need to do gksudo grsync to avoid permission errors??

The external disk partition for my clone backup is mounted at /media/FrodoFullBackup and I have created a folder on this partition called backup.  So the path to where I would like my clone backup to go to is /media/FrodoFullBackup/backup.

For the source would I use: // 
For the destination would I use: /media/FrodoFullBackup/backup/

Will this take my entire file system and clone it within the /media/FrodoFullBackup/backup folder while maintaining the existing filesystem structure within the backup folder?

Also /media is part of my filesystem that has other external drives that I do not want to backup, therefore do I need to include:
--exclude=/media

Sorry for being painful but I would rather ask the questions first and be clear what I need to do before stuffing everything up!

Thanks

Peter

---

### Post by Richardcavell on 2009-07-02
Yes, gksudo grsync is best. I've added it to my Applications/System Tools menu. There is an option under 'Basic options' for 'Do not leave filesystem', which will prevent rsync from going into mounted drives.

Richard

---

