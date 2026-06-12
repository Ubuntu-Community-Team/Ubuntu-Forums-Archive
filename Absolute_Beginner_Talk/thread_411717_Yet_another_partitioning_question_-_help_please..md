---
title: "Yet another partitioning question - help please."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by knockerwhite on 2007-04-17
I am a brand newbie......
I want to install Ubuntu on my Sony Vaio laptop.  It came partitioned with Windows XP on the C drive and a D drive, presumably for data.
I have cleared all my files from the D drive as I want to install Ubuntu on this partition, leaving XP clear on the C drive.
Problem, during the Ubuntu installation, when I reach the partitioning screen, it only seems to see the C drive, thereby not allowing me to select the D drive for installation.
I have read an awful lot about Linux and desperately want to get it up and running....help in simple terms please.

Thank you.

---

### Post by aberry5555 on 2007-04-17
Is there any chance of posting a print-screen of the installation at this point, also could you go through the menus and find a terminal (im sorry but off the top of my head I can't remember where it is, only that it's in one of the "start" menus). Once you get it up type

```
fstab -l
```

(the -l being a lowercase L)

and post back what it says along with the picture.

---

### Post by Tundro Walker on 2007-04-17
Don't mean to butt in, but wanted to add a correction...

(Main Menu) > Accessories > Terminal

```
sudo fdisk -l
```*fstab* is the config file, *fdisk* is the command to list the drives.  Gotta use *sudo* to run it as super-user, or else you won't get anything back.

I'll butt out now.

---

### Post by Kobalt on 2007-04-17
Here is an excellent step by step and illustrated guide to planing partitions : [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Welcome to Ubuntu :)

---

### Post by knockerwhite on 2007-04-17
Thank you all for your speedy responses, most impressive!  Makes me want to join the community even more.
Unfortunately, I am at work and don't have access to my laptop.  Will have a go this evening though.
Having read the links suggested by Kobalt, I think I am going to have get rid of my D partition by extending the C?  If I can do this, I think the installation should be fairly straightforward..........will let you all know.

knockerwhite

---

### Post by antoz on 2007-04-17
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

Here is an other good link that might be helpfull

---

### Post by bodhi.zazen on 2007-04-17
Partitioning is confusing at first and it does not help that windows and Linux use different terminology.

Here is a  link to a summary of partitioning terminology : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

It is important to understand so you do not overwrite your windows install.

For Ubunutu you need at lease 2 partitions : swap and /

Size of swap = RAM X2, max 1 Gb

/ = partition to install into. Size min = 5 Gb, although 10-20 would be nice.

You should also consider making a FAT partition to share data between windows and ubuntu, although this is not necessary.

So that would give you 4 partitions:

/dev/hda1 = windows
/dev/hda2 = FAT share
/dev/hda3 = ubuntu
/dev/hda4 = swap

Obviously there is more then one way to partition your HD, this is just some general advice.

---

### Post by dstew on 2007-04-17
If you are using GParted to make your partitions, you will need to use the Linux names. Unlike Windows, which uses letters like C: and D:, Linux uses names, like /dev/hda1. If your Windows partition (C) is the first one on your first hard disk, the Linux name will be /dev/hda1. Usually, you do not get rid of a partition by expanding the adjacent partition. In GParted, you delete the partition you do not want. Then, your disk will have unallocated space. You then create new partitions in the unallocated space.

If your disk has two partitions, and you want to install Linux on one, my guess is that Windows will be in /dev/hda1, and the other partition will be /dev/hda2. It is good to have at least two partitions for a Linux system, a root partition and a swap partition. If this is what you want, then leave the Windows partition alone, and delete the second partition /dev/hda2. Then, make two new partitions out of the unallocated space, a small swap partition about twice the size of your RAM, and another partition for your Linux system. Leave the swap partition unformatted, and format the new Linux partition as ext3. Give the ext3 partition the mount point root ('/'), and leave the swap partition unmounted. Then go ahead and install.

---

### Post by thefoolisme on 2007-04-17
I was just wondering if the D drive held your system backup/restore files for your Windows install, or do you have separate CDs for that?  So many laptop manufacturers now simply put the restore info in a separate partition.  

Be sure to back up any important data before starting all of this, so you are not at risk of losing vital information.    

Good luck with the install.  I think you'll have fun with Ubuntu once you get it up and running.

---

### Post by aberry5555 on 2007-04-17
woops, you're right, fdisk -l, not fstab hehe

---

