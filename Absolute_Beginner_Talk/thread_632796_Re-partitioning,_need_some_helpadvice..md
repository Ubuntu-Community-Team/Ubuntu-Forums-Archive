---
title: "Re-partitioning, need some help/advice."
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-12-05
Okay, as of right now, I have four primary partitions.[list][*]Windows Vista (sda1, 20GB)[*]NTFS Volume used as a network share for my family (sda2, 430GB)[*]Swap (2GB)[*]Kubuntu (48 GB)[/list]

Now, the only thing I personally have used the Windows Partition for in the last two or three months (as long as I've had the computer) is to download Kubuntu and resize my partitions for the Kubuntu installation.  I kept it on there as a fallback OS, and because (when it was upstairs and being used as a family computer) my mother used it for her schoolwork (she needed Shockwave, and I was having some trouble getting it to work in Windows Firefox under Wine).

However, since my Kubuntu system is now fairly stable, and I've been successfully weaned away from Windows for quite some time (except for this post--at work we still use Windows, but I'm getting them to go Open Source with their programs at least!), I would like to remove Windows completely.  Also, I would like to make a seperate partition for my /home directory, as it's been advised for both backup and upgrades.  Heh.  Finally, I would like to install another Linux OS on my computer (both Arch and Gentoo have been suggested for my needs {basically, exploring Linux, getting to know it better, maybe start developing for it if I can}).

Question one: Can my new /home partition be used with both Ubuntu -and- another distro?  What kind of complications might there be?

Question two:  Partitions will now be[list][*]Kubuntu[*]NTFS Share[*]New Distro[*]Home[*]Swap[/list]As you have noticed, that leaves me with the complication of making extended partitions.  Which partitions, in your opinion, should go into the extended partition and why?

Question three:  Can my Swap can be used for my other Linux distro?

Question four: What is the aerial velocity of an unladen swallow?

Question five:  What would be the complications involving changing the 400GB NTFS volume into something more native to Linux (about 200GB of said volume is full), and (other than less complications) would it gain me anything in the long run (e.g., better use of storage space)?


Finally, I might like to try out several other distributions as well in the future, and would like to take this into consideration in my partitioning scheme.

---

### Post by LaRoza on 2007-12-05
> **Sarteck said:**
> 
Question one: Can my new /home partition be used with both Ubuntu -and- another distro?  What kind of complications might there be?

Question two:  Partitions will now be[list][*]Kubuntu[*]NTFS Share[*]New Distro[*]Home[*]Swap[/list]As you have noticed, that leaves me with the complication of making extended partitions.  Which partitions, in your opinion, should go into the extended partition and why?

Question three:  Can my Swap can be used for my other Linux distro?

Question four: What is the aerial velocity of an unladen swallow?

Question five:  What would be the complications involving changing the 400GB NTFS volume into something more native to Linux (about 200GB of said volume is full), and (other than less complications) would it gain me anything in the long run (e.g., better use of storage space)?

Finally, I might like to try out several other distributions as well in the future, and would like to take this into consideration in my partitioning scheme.

For a multiboot machine, make small partitions, I used 10 GB logical drives. You can add distros to those partitions, I don't know how many you want, so I can't give a number to make.

It doesn't matter what is in the extended partition, I would make a large extended partition, divide it into logical drives (as stated above), and use them for the / of the various distros.

Swap can be used by others.

It depends which way it is flying, and the weather conditions, "man swallow".

To keep things simple, I would leave the partition as NTFS. Ubuntu 7.10 can use it fine. In the future, use ext3. If you have the time (space) to move all the data for a reformat, you can do that.

In the end:

sda1: Extended Partition - Make large enough to hold all you distro's /,
sda2: Primary Partition: /home
sda3: Primary Partitions, whatever you want for storage, NTFS
sda4: Primary Partition, swap, 512 MB.

The actual numbers and order is up to you of course, this is what I would do.

---

