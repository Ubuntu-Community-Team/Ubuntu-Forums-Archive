---
title: "[SOLVED] Formating an External Hard drive"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by caoinan on 2007-08-28
I am having a problem trying to format my external hard drive.  Its actually a laptop hard drive that my dad made into an external hard drive but I cant seem to get rid of all the partitions so it can be just one partition I attached a pic of what it looks like in Gparted.  So what I want to do is get rid of all the partitions and then re-format it in fat 32 but I cant seem to get rid of the other partitions.

---

### Post by Anzan on 2007-08-28
I don't know much about this but it probably has to do with permissions.

sudo this:

chown -R yourname fileordirectory
chmod -R 777 fileordirectory

---

### Post by caoinan on 2007-08-28
ok I did that  now what.  what program do I use to format the drive and can I format the whole drive without having to do the separate partitions

---

### Post by caoinan on 2007-08-28
and how do I change my permissions so I can mount and unmount cause when I try to use Disk Management it says  
> There are no filesystems which you are allowed to mount or unmount.
Contact your administrator.

---

### Post by Anzan on 2007-08-28
I think you should just try it again with Gparted now. Good luck.

---

### Post by caoinan on 2007-08-28
uh there isnt the option for me to format it in Gparted  when I right click all the options are greyed out except  Unmount,   Manage Flags,  and Information

---

### Post by dwhitney67 on 2007-08-28
Do you know where the drive is mounted?  Is it using perhaps a USB connection?

You can use **fdisk** to wipe out any existing partitions and then create new ones.  You probably want to setup an extension file system.

Usage:

[FONT="Courier New"]$ sudo /sbin/fdisk /dev/<xxx>[/FONT]

where <xxx> is the device where the drive is mounted.  For a USB, it is probably sdb1, sdb2, etc.

Your primary HDD is probably /dev/sda1.  You can find out by running the command "mount".  Don't fdisk your HDD!!!!

After you have setup the partition on the external drive, you can format it to be an ext2 (extension 2) file system, but it might not be necessary because if I recall fdisk takes care of that.  In case it does not, here is the command:

[FONT="Courier New"]$ sudo mke2fs /dev/<xxx>[/FONT]

---

### Post by caoinan on 2007-08-28
here is what it says when I type:  sudo /sbin/fdisk /dev/sdb2

```
The number of cylinders for this disk is set to 3641.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```
so what do I do here? and what would would be best for me format it to?

---

### Post by caoinan on 2007-08-28
...

---

### Post by MQMike on 2007-08-28
In Gparted, just click on each partition, then select Delete.  Do this for each partition.  Click Apply. Then highlight the unalocated space. create a partition.  Format it (during creation of Partition), or  Format it under Partition-Format.  This shouldn't be a problem

---

### Post by caoinan on 2007-08-28
ok I'll remember that but I need to change the permissions of my account so I can mount/unmount devices  since I dont have that permission I think that is what is preventing me from being able to format it and make a partition. whenever I'm in Gparted all of the options are greyed out when I right click the partitions except for unmount, manage flags, and information.

---

### Post by caoinan on 2007-08-28
ok I got it so what would be the best format for my external drive or does it really matter  if i use ext3, fat32, ntfs ,etc

---

### Post by dwhitney67 on 2007-08-28
> **caoinan said:**
> here is what it says when I type:  sudo /sbin/fdisk /dev/sdb2

```
The number of cylinders for this disk is set to 3641.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```
so what do I do here? and what would would be best for me format it to?

For starters, type 'm' for help.  Then 'p' to list the partitions.  To delete a partition, use 'd', and then specify the partition number (1-4).  To create a partition use 'c' and then the size.

Since I do not have a spare drive to practice with, all of the above is drawn from memory... that is my memory... not my PC's!

---

### Post by caoinan on 2007-08-28
ok well I got it now I just want to know what  format would be the better format (if i'm using it on windoz and linux) ie fat32. ext3, ntfs, etc

---

### Post by dwhitney67 on 2007-08-28
you can use NTFS.

---

### Post by diatribe on 2007-08-28
I would use fat32 if using it for windows also or ext3 for linux, ntfs is excessive work to get working properly

---

### Post by caoinan on 2007-08-28
aight thanks

---

### Post by dwhitney67 on 2007-08-28
> **diatribe said:**
> I would use fat32 if using it for windows also or ext3 for linux, ntfs is excessive work to get working properly

It was a "bunny" for me to get my NTFS drive working.  There are clear instructions on how to do it.  I do not quite understand why everyone is having so much trouble.  Here's the link to the [instructions]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html").

---

