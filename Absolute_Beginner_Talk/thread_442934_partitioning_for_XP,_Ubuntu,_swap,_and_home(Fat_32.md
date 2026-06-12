---
title: "partitioning for XP, Ubuntu, swap, and /home(Fat 32)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by godssiren on 2007-05-14
I was reading the [psycocats]("http://www.psychocats.net/ubuntu/partitioning") install page about partitioning. And after reading all the posts on it I could find that seemed relevant, I would really like to set up my hard drive with one partition for XP, one for Ubuntu, a swap for Ubuntu, and a home drive for shared files. But I'm not too experienced with mounting drives or partitioning. I didn't know if there was a more detailed tutorial on how to set my computer up like this, or at least something to help me understand more about what i'm doing so that I don't mess something up. ^_^ any help is appreciated.

---

### Post by godssiren on 2007-05-14
also forgot to ask whether the basic Ubuntu installer would be ideal for this, or if there is a simpler program?
Thanks.

---

### Post by dfreer on 2007-05-14
well, that guide looks like it explains things pretty well. do you have any specific questions about it or partitioning that we could help answer? the method that you mention you want to use will work just fine, make sure to partition the HD then intall xp first to save yourself heartache later. cheers and welcome! oh yeah swap should be 1.25 times the amount of RAM you have, so 1.25 GBs for 1 GB of ram.

EDIT: the basic desktop live cd is the simplest installer, although not the only method.

---

### Post by godssiren on 2007-05-14
so if I want  to partition it this way then I will have to re-install windows? or just make it the first portion of the partition? and with a dual boot system, if i want a login screen to choose which to boot when I turn on my computer, do I need to put that program first? (ie, lilo - can't remember the name of the one on the live CD)

I guess my other question is, how easy will the program on the Live CD maker it to partition the drive in this way for someone who isn't too experienced? The tutorial I mentioned in the first post makes it seem like if I want to set up a home drive for shared files that I have to configure manually. And I don't have a problem with that except I'm not sure what I'm doing.
^_^'


The basic problem is that I want to be able to easily access my files from both Windows and from Ubuntu. And from what I've been reading, that will be easiest with a separate partition from the OSs. It seems like it would also help if I ever need to reinstall one or both of the OSs, because I won't lose my info.

---

### Post by alienexplorers on 2007-05-14
I use to have just a 40GB drive and had both Windows XP and Ubuntu loaded.  My partitions were as follows:

> Windows  NTFS partition 10GB
Windows Data FAT32 Partition 10GB
Ubuntu Partition ext3 partition 10GB
Ubuntu Home ext3 partition 9GB
Swap partition 1GB

These sizes can be adjusted higher or lower as per your preference.

A short file on mounting partitions can be found at:

> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by godssiren on 2007-05-14
> **alienexplorers said:**
> I use to have just a 40GB drive and had both Windows XP and Ubuntu loaded.  My partitions were as follows:


These sizes can be adjusted higher or lower as per your preference.

A short file on mounting partitions can be found at:

So you would suggest that I have a different file area for each OS?  
 
I think I get the general idea of how I need to partition the drive, but I don't know what the stuff in this image represent.
[http://www.psychocats.net/ubuntu/images/feistyd.ualthumb10.png](http://www.psychocats.net/ubuntu/images/feistyd.ualthumb10.png) 

ie, I don't know what "/dev/hda1" is in relation to the computer partitions. I tried to search the forums and the web for it but couldn't find anything that clarified it much for me.
Sorry, I feel a bit foolish having to ask, but I'd much rather understand it than just go for it since this is currently my only working computer.

---

### Post by HumbleGod on 2007-05-14
I'm relatively new to Ubuntu, but here's the setup I'd recommend if you plan to use the OS regularly:

A small NTFS partition for Windows programs and data
A small-to-medium EXT3 partition for Ubuntu OS and program files
A large EXT3 partition for your Ubuntu /home directory
~1 gb swap partition
Optional: A small FAT32 partition for transferring files between Win and Ubuntu

I use this setup because I don't use my Windows system too much anymore, I don't need a lot of apps in Ubuntu, and I store most of my data on the /home partition. (To help, there's a Windows utility called FS-Drive that allows read/write to EXT3 from within Windows; I'll let you find the URL since I'm too lazy to look it up right now, but it's relatively popular here.) The point is, your mileage may vary--your needs may require more space for Ubuntu apps or Windows things.

As for /dev/hda1 and all that....your hard drive is hda. (A second would be hdb; an SATA drive would be sda, etc.). hda1 is the first partition on your hda drive, hda2 would be the second, etc.

Unless things go utterly bugf*ck (an unlikely prospect), you shouldn't need to reinstall Windows. Just make sure you have enough free space on your NTFS partition to shrink it to make room for the others.

---

### Post by HumbleGod on 2007-05-14
Also, another thought. I'm not a big proponent of huge FAT32 partitions for storing shared data. FAT32 isn't the greatest file system--it's very inefficient, defragmentation can be a pain, and it has a 4gb ceiling (which is no good if, like me, you have DVD .iso files in your system from time to time). FS-Drive makes it pretty much irrelevant anyway, but I still keep a 500mb FAT32 partition in case of hard times.

---

### Post by alienexplorers on 2007-05-14
Do you already have XP loaded.  If so, you may need to resize the partition using gparted to make room for ubuntu if using a small drive.  Run gparted from your Live CD.  Make a Data Partition for Windows in Fat32 format.  Leave the rest of the drive unused.  Install Ubuntu and when your get to the partition part select manual partition.
Make 10GB or so the root partition in ext3.  Make a /home partition in ext3 in whatever size suits you.  Save 1 or 2 GB as a swap file.  Allow Ubuntu to continue loading.  It will setup grub for dual booting.  When done you need to boot Ubuntu and then you have to setup a mount to the Windows Data Partition.

> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

This is done by editing your fstab file.  To edit it enter in terminal:

> gksudo gedit /etc/fstab

then run:

> sudo mount -a

This will mount your new windows data partition and make it readable and writeable
from Ubuntu.

---

### Post by ticklj on 2007-05-14
In installing Ubuntu (successfully) the grub loader (first stage) was put into the MBR. The installer
did not (I think) give me the opportunity to request it be placed in the boot partition. How does one do that?
Do I need to reinstall to do so .
Thanks

---

### Post by dfreer on 2007-05-14
Use the alternate CD to install if you wish to specify whether to install GRUB to the MBR or not.

As for OP:

If you already have windows installed, do you have it using the whole HD or is it in a small enough partition so that you can install Ubuntu on the HD as well? You CAN share a fat32 partition between the two OS, using it as your home/My Documents even. That way you will have: 
1 Windows OS Partition (min 10 GB's)
1 Ubuntu Swap Parition (around 1.25 X total RAM)
1 Ubuntu / Partition (min 4 GB's)
1 FAT32 shared partition (In the top folder, I would put a My Documents Folder and a Home folder. From there, map your my documents in Windows to the My Documents folder on the FAT32, and map your /home/$USER/ folder to your Home folder on the FAT32. This is just an one example of ways to do this, but really you should get to know more about partitioning, mounting, and system links if you want to share your My Documents/Home folder's across OS's)

you'll need to read up on what /dev/hda1 means, but basically hd means an IDE driver (sata, flash, and USB drives will be sd), a stands for the first hard drive (b would be the second, c the third and so on), and 1 stands for the first partition on the drive (1-4 are reserved for primary partitions, 5-X stands for logical paritions).

---

### Post by godssiren on 2007-05-15
Ok,
so I used the partition link and instructions to help me figure out what I have right now using G Parted.
When I opened GParted while running my liveCD I saw the following:

/dev/sda2 !  fat32           4.18  GiB       ---
/dev/sda1    ntfs           70.34  GiB     (40.23 GiB used, 30.11 GiB unused, "boot" under flags)
unallocated  unallocated 7.84   MiB      ---
 
After doing some reading on the forums and the suggested pages, I took a look at this and realized that the sda2 was my "backup" partition windows had created to help me restore windows if ever it crashed.(they were prepared, how cute) and the sda1 is the main partition.

Now I was a little surprised that the windows area had 40.23GB used, but I also noted that it has the rest of the HD allocated to it.

So, what i've gotten from all this, is that I need to resize my windows partition, so that I have more free(unused) space, which I can then allocate to Ubuntu, the swap, and a home/my documents partitions. 

Am going to have to leave my  windows partition at 40+ GB in order not to lose data?
A lot of that 40GB is just my pictures and music, (and programs, games etc) that I would like to end up on the home partition at some point. 
Can I create the Ubuntu, swap, and home partitions and then resize the windows partition once I've moved my personal files to the home partition? (and once I do, can I make the home partition bigger to include the newly freed space while my files are still on it??) 

Lol, I'm loving all this, even as frustrating as it is. I am getting more and more sucked into the forums, however for every answer I find, more questions pop up!  ^_^'

---

### Post by dfreer on 2007-05-15
Yes, you'll probably want to defragment your windows drive (If you have a nice defragmenter, make sure it moves all files to the beginning of the drive) first, and then resize the partition. you cannot resize it smaller than the amount of space used, and I would leave about 2 GB's of padding space (windows won't run very well if you use up ALL the hard drive space available to it). That should free up about 28 GB's, you could just create a FAT32 parition in that free space and start moving all your music/videos over to it in windows. resize again if needed. Then, once everything is on the FAT32, you should be able to comfortably resize the windows partition and install 2 more partitions, one for ubuntu and one for ubuntu swap.

Even though it is frustrating, anytime you try resizing a hard drive you are risking that you will mess your partitions up, essentially losing your data if you don't know how to fix it. The best advice would be backup your data to another hard drive or DVD, wipe windows (backup any drivers first! Dell like to put them in C:\DRIVERS\, and HP puts them in some huge folder on the C:\ as well, I just can't remember where), partition the hard drive entirely the way you want it, reinstall windows then install ubuntu.

---

### Post by godssiren on 2007-05-15
> **dfreer said:**
> Yes, you'll probably want to defragment your windows drive (If you have a nice defragmenter, make sure it moves all files to the beginning of the drive) first, and then resize the partition. you cannot resize it smaller than the amount of space used, and I would leave about 2 GB's of padding space (windows won't run very well if you use up ALL the hard drive space available to it). That should free up about 28 GB's, you could just create a FAT32 parition in that free space and start moving all your music/videos over to it in windows. resize again if needed. Then, once everything is on the FAT32, you should be able to comfortably resize the windows partition and install 2 more partitions, one for ubuntu and one for ubuntu swap.

Even though it is frustrating, anytime you try resizing a hard drive you are risking that you will mess your partitions up, essentially losing your data if you don't know how to fix it. The best advice would be backup your data to another hard drive or DVD, wipe windows (backup any drivers first! Dell like to put them in C:\DRIVERS\, and HP puts them in some huge folder on the C:\ as well, I just can't remember where), partition the hard drive entirely the way you want it, reinstall windows then install ubuntu.

I have defragmented my drive about 10x with Windows in house defrag program... problem is, I do this pretty often, so it didn't do much. And it won't move all of the files to the begining of the drive.
It comes out looking something like [THIS.]("http://021805.tripod.com/photosnstuff/index.album/i-really-dont-like-ms-today?i=1")

Where the Blue  is the contiguous Files, the Green are unmoveable files, and the little strip of red is the fragmented Files...

The majority of the first half of the drive shows up as almost solid... However, it still has files(blue) and a green area (unmoveable) at what looks like the middle to end of the drive, and Windows doesn't allow for me to move it. (if they correctly graphically represent their own system) 
[COLOR="Red"]If I use GParted to shrink the partition, I will only be able to make it as small as the farthest point with data on it, right? Or will GParted move that back with the rest of my data when I ask it to shrink the partition(so long as the total space used is still less than the size I ask it to shrink to)?
Is there another program I can use which will move all the files to an earlier part of the drive so that I can resize it easier? [/COLOR]

 I think I would like to try transferring my files to a different partition and then resizing the main one to be even smaller, because although I have backed up  my files with both Nero, and the windows Backup, I want to create a straight data CD, because both the others gave me problems that make me worry about the condition of the back up.
[COLOR="Red"]Any suggestions on a better way to do this?[/COLOR]

---

