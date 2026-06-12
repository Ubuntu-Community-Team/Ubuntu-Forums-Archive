---
title: "Removing Vista from Dual Boot Setup"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-10-24
I have a dual boot setup with Vista and Fiesty right now. My partitions are as follows: C: (Vista - NTFS) D: (Data partition for storage - NTFS) and then Ubuntu. I want to remove Vista and expand the size of my home directory in Fiesty. If expanding the home directory is not possible, than I would like to add the extra space to my Data partition. What is the best way to accomplish this? Is it as simple as using GParted to delete the Vista partition and then add the unallocated space to the home directory or Data partition.

Also, I did not create a seperate home directory partition when installing Ubuntu. I allowed it to use the free space I had available on the disk. Will this mean I can not expand the home directory size?

---

### Post by LaRoza on 2007-10-24
The *easiest* thing to do is a reinstall, and use GParted to make the partitions just the way you like it.

If this is not possible, or practical, you can reformat the Windows partition, which I am assuming is larger than the data partitions, move the data to this partition, delete the data partition and expand the new data (old Windows) into the new space.

Remember to back up, and fix fstab after doing this.

I would take the time to resinstall, if you didn't have an special programs or configurations you might not be able to replicate. You can copy the contents of your home directory to the new one to save your settings.

---

### Post by jba6511 on 2007-10-24
> **LaRoza said:**
> The *easiest* thing to do is a reinstall, and use GParted to make the partitions just the way you like it.

If this is not possible, or practical, you can reformat the Windows partition, which I am assuming is larger than the data partitions, move the data to this partition, delete the data partition and expand the new data (old Windows) into the new space.

Remember to back up, and fix fstab after doing this.

I would take the time to resinstall, if you didn't have an special programs or configurations you might not be able to replicate. You can copy the contents of your home directory to the new one to save your settings.

My data partition is 100+ GB and my Windows Vista partition is around 30 GB. I do not want to delete the data partition, just the Windows Vista partition.

---

### Post by jba6511 on 2007-10-24
Since my Windows partition is first, I am assuming I will not be able to use GParted to add that space to Ubuntu or my Data partition. Can I just make this an ext3 file system and then move my home directory to this partition? So it would look like this:

_New Layout_
/home directory
Ubuntu
Data

_Old Layout_
Vista
Ubuntu
Data

---

### Post by jba6511 on 2007-10-25
anyone??

---

### Post by vexorian on 2007-10-25
Resizing home is not as simple and thus it would be better to try a backup + reinstall

You may just format the vista partition with ext3 or even ntfs , then you can make a symlink in /home to the extra storage section.

---

### Post by jba6511 on 2007-10-25
so there would be no issues with having the layout look as follows:
ext3 (used for storage)
data (ntfs)
ubuntu

Will this affect GRUB or etc/fstab by doing this? How do you create a symbolic link to ext3 partition?

---

### Post by vexorian on 2007-10-26
As long as you don't touch your / partition this won't have an effect on grub (although there might remain a vista ghost in the menu, which you will have to remove)

well, your storage partition will just act like some external USB drive, you know, you will be able to have folders there.

A symlink you don't really have to do it unless you want to redirect certain tools to use it when they are doing things in /home. 

It is something like ln -s /media/sdb1/myfolder ~/myfolder

provided your ext3 partition is sdb1 and the folder you are creating is myfolder...

---

### Post by mdpalow on 2007-10-26
Hello,

I'm very new to Ubuntu, but would like to reply to this message as well.

Since you plan on removing Vista anyways, it would seem almost as easy to just reinstall Ubuntu 7.10 with a clean copy since it takes less than 20 minutes including formatting your new partitions.

Based on what I have read in the forum, this is how I did it.

Partitions:

1st:    /               [ 50 gigs using ext3 file format for system files]
2nd:   /home       [ 145 gigs using ext 3 file format for /home directory]
3rd:   /windows   [ 2 gigs using Fat 32 file format]
4th:   /swap        [ 3 gigs using ext3 file format ]

Since you plan to remove Windows entirely, you can leave out the /windows partition. All of this can be done using the install disk again and selecting MANUAL when the option to partition comes up. I read that it's good to make your swap drive twice as big as the amount of RAM you have.

Since backing up and restoring your /home directory is so simple (see thread 35087], just seems - IMHO - to do it this way with a clean install.

Also, when partitioning - just delete all the partitions you currently have and that will free up everything. Then edit the partition to make them how you want. I'm assuming you have one HD and want it all Ubuntu. Also, when you delete all the partitions and then add them back, they will all be in order.

Good luck...

---

### Post by jba6511 on 2007-10-26
well guys I think I am going to go ahead and do a clean install. Will be starting another thread on partition layout. Thanks

---

