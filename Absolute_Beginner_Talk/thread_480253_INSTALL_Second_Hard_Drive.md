---
title: "INSTALL Second Hard Drive"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by BeauBobbitt on 2007-06-21
Have looked and, as a newbie, could not find exactly what I need.  I have latest (7.04) installed - running perfectly - machine has 20 GB drive - have purchased WD 800 80GB drive to add as second drive.

Are there step by step instructions on the forum?  I have done this MANY times in WIN-XP and understand formatting, FDISK etc.  How is this done in Feisty? - again step by step.

I am sure it is out there - I just cannot find it.

---

### Post by overdrank on 2007-06-21
> **BeauBobbitt said:**
> Have looked and, as a newbie, could not find exactly what I need.  I have latest (7.04) installed - running perfectly - machine has 20 GB drive - have purchased WD 800 80GB drive to add as second drive.

Are there step by step instructions on the forum?  I have done this MANY times in WIN-XP and understand formatting, FDISK etc.  How is this done in Feisty? - again step by step.

I am sure it is out there - I just cannot find it.

Hi and welcome, I just installed a second drive to a system the other day and if you have the jumpers set right on the drives it should be easy. Just add the drive ( I assume you have the drive set as slave to the existing drive) Then you can install via the terminal *sudo apt-get install ntfs-config* and that should mount your drive and you are ready to go. Hope this helps and good luck!:popcorn:

---

### Post by martnemma on 2007-06-21
I think they are on about installing as a native drive using gparted etc. newbie myself so not too sure on the commands needed only done it ONCE.

Install QTPARTED if not already and use that to partition the drive as a linux partition you may not sure here have to create a mount point to the drive, but not sure on how to do this maybe someone else can help here.

You'll probably have to reboot the system for the drive to be seen - although this may not be true.

Good luck

Martin

I have also used the command line too but thats a lot more complicated, but you can do more.

---

### Post by trak87 on 2007-06-21
I don't have a link providing step by step instructions at the moment -- a search on this forum will turn up something like that -- but it's pretty simple. After you get the drive installed it's a matter of creating a partition and then formatting it with the file system of your choice. The first thing to do is determine the drive device name:

```
sudo fdisk -l
```

(that's a lowercase -L)

You'll see your original drive (probably /dev/hda) and the new drive, let's say it's /dev/hdb.

Next you can use fdisk to create one or more partitions: "sudo fdisk /dev/hdb". Then there are different commands to create the filesystems on each partition. For example, if you want ext3 on your partition, and the disk partitions are at at /dev/hdb1 and /dev/hdb2 use "sudo mkfs.ext3 /dev/hdb1" and "sudo mkfs.ext3 /dev/hdb2".

If you'd rather use a gui, "gparted" makes this whole process easy and it's in the repositories. Just install and run it. If you ever used Partition Manager by PowerQuest in the Windows/DOS world, gparted looks a lot like that.

---

