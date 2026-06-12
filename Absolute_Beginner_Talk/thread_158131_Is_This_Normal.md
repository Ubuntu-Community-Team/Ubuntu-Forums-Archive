---
title: "Is This Normal?????"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-10
I was just looking at System>Administration>Disks and looked at my hard drive.
This is what it said: Properties:                                 
                           Samsung SP1604N
                           149.05 GiB
                           /dev/hda
            
                           Partitions:
                           Partition 1: / (ext 3) 146.15 GiB
                           Swap Partition: 2.9 GiB

Is this normal? bBecause I've seen people with /boot partitions and root partitions and other weird things.  I just did the default "erase entire disk and create partitions" during the partition process of the install!!!

---

### Post by x5452 on 2006-04-10
i believe so, i did the same erase entire disk option when i installed ubuntu, and it takes a small portion of your hard drive to use as swap, which, depending on how much memory you have, i think it doesnt really use anyway.  but im not sure. and it partitions the rest to home (/) for all your files ect to go

---

### Post by taurus on 2006-04-10
You should be okay.  There are many ways to partition your harddrive to install Ubuntu but as long as it works, don't worry about it.  You are using the default while others use the manual to partition their harddrive to whatever they want...  Some even have a seperate partition for /home.  :)

---

### Post by bscbrit on 2006-04-10
It should be fine - but I don't imagine you will ever need quite that large a swap partition.  But you seem to have plenty of spare room on your drive so it will not be a problem. :D

---

### Post by az on 2006-04-10
[QUOTE=x5452] and it partitions the rest to home (/) for all your files ect to go[/QUOTE]

/ is the root directory.  /home is the home directory.  /root is the home directory for the root user, but ubuntu does not enable the root user by default.

Anyway, all-on-one-partition is the ideal situation for a desktop.  You don't run the risk of running out of disk space and it makes the all-too-complicated installation all the more simple.

The installation is a big hurdle for many users who are migrating from other operating systems.

The benefits of making several partitions is only significant for some very specific purposes, such as not having your server crash because you ran out of disk space because someone kept spamming you.

Some advocate a separate home partition.  I don't find that to be apealing, since a lot of the misconfigurations that would make a user want to reinstall will be brought along to the new installation.  You rarely need to reinstall anyway.  It's a lot easier to just make a proper backup of your important files.

---

### Post by user1397 on 2006-04-10
Alright thanks guys I got just what I needed :cool:

---

### Post by angkor on 2006-04-10
[QUOTE=azz]Anyway, all-on-one-partition is the ideal situation for a desktop. [/QUOTE]

I prefer having a seperate /home partition on my desktop systems. Very convenient when reinstalling ;). I was also able to come from Debian to Ubuntu and keep the same /home partition. :shock: all settings were still the same/

 Just make sure, like azz said, that you've got enough space for your root partition.

---

