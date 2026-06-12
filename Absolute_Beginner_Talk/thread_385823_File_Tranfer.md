---
title: "File Tranfer"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Brick86 on 2007-03-16
Hi, I would love to switch over to ubuntu from my windows xp pc.  I know how to install it and everything but I was wondering how to keep my files on the HD so that I can use them in ubuntu.  It is mainly music/ movies.  Note that the files I want in ubuntu are on the HD now.  What do I do?

---

### Post by Kobalt on 2007-03-16
What you can do, very simply from the Ubuntu LiveCD, is to create a FAT32 partition on which you'll place everything you want to access both from Ubuntu and Win. 
Both will see, mount, read and write that partition automatically...
Here is some additional doc on planning your partitions, I highly recommend you to go through this before you touch anything.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by eljalill on 2007-03-16
Or an ext3 partition (for which you would have to install drivers in Windows), since ext3 is a more up to date format..

---

### Post by Brick86 on 2007-03-16
I am sorry for any inconvinience but I am very new to this.  I am not sure what you mean by making a partition.  I'm sure it is just a way to share files between files from windows and files from ubuntu but I would like ubuntu to be the only OS on my computer.  If you wouldn't mind explaining how to do this in the easiest possible way, that would be great.  Thanks!

---

### Post by MikeSz on 2007-03-16
In simlpe terms...a partition is a segment of your hard disk drive.  think of slicing up a cake.  When you partition a hard disk, you create manageable 'chunks' for your system to use and to do that, your computer has to introduce a file system in order to store data.  Windows has traditionally used a system called FAT (or File Allocation Table) which then evolved into FAT32, then later there came NTFS (New Technology File System).  These are essentially ways of storing data on your hard disk drive, though it there are also benefits and down sides to using each.  for more info on file systems have a look at the link ive pasted below.  Linux uses Ext3.

[http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)  

So, the general point is, as there are different kinds of partitions you can use, you need to decide what you want running on your computer and how much space you will want for everything - does that kinda make sense?  When you install Ubuntu, you will have the option to set aside a partition or decide how much space you want your Ubuntu partition to take up.

does that help?

---

### Post by akudewan on 2007-03-16
Hi,

Suppose you have a c: drive and a d: drive in windows. These may not be separate Hard disks, but partitions on the same harddisk.

In linux, we don't call these c: and d: but hda1 and hda2. (HardDisk-a-1, HardDisk-a-2).

So what you can do is: Put your files into one partition ( d: ), and install ubuntu on the other ( c: ). Windows should be in c: by default.

However, I strongly recommend that you make backups of your data on CDs or DVDs or something, because incase something goes wrong, you'll have a bad time...

---

### Post by Kobalt on 2007-03-16
Allright, my mistake : I thought you wanted to keep Windows and install Ubuntu aside. If you wish to completely move from Win to Ubuntu, it is good news, but you might want to consider a dual boot in my opinion, especially since you seem a rookie Linux user (with all due respect). Would you mind answering a few of these questions so that we can tell you if a dual boot is wiser than a straight away move...
Do you play games ? How do you connect to the internet ? What programs do you mainly use on your computer - and what other programs do you have that might be rare, exotic, etc. ?

---

### Post by Brick86 on 2007-03-16
Thanks a lot! I do play games but basically on nothing but the internet.  I dont play computer games from discs.  I tend to use things such as the internet, office 2003, and things such as AIM.  I also like to edit photos and watch movies.  I have used the live cd for a while now and I have found that anything that I would like to be able to do tends to be here.  The only software that I would hope they would have would be WMP  and Zune software.  They may (I don't know), but I am willing to get rid of them for ubuntu.  What next?

---

### Post by Kobalt on 2007-03-16
WMP and Zune software are microsoft apps, they're very unlikely to be ported on Linux (or maybe when dogs will read the newspapers). 
How about your internet connection ? 
When you write about internet games, I guess you mean games based on flash or java ? That should be ok now on Ubuntu, since Flash 9 and Java 1.6 are now available for Linux.
So far you don't seem to have particular needs that might not be fulfilled by Ubuntu...

---

### Post by Brick86 on 2007-03-16
I connect to the internet wirelessly (I have a laptop).  I also use IE7 but I would actually prefer firefox for its safety.

---

### Post by Kobalt on 2007-03-16
All right, here we are : wifi. 
Do you know the model of your wifi card ? Some are supported by Ubuntu natively : did yours work in the LiveCD session ? If so, you're lucky and you'll be happy to move on to the installation of your Ubuntubox. If not we need to know the model so that we can help you install it properly. 

I still recommend you to use a dual boot at first : you might have, some day, the will to play a game or the need to use an app that's windows only. That day, you'll be glad to have kept your win installation.

---

### Post by Brick86 on 2007-03-16
Sorry, I didn't realize this went to a second page.  I am actually on the live cd now and I have been for this entire post. 
Everything is working flawlessly for me. I do have a copy of windows xp cd which can still be used if anything was to go wrong.  Anything else?

---

### Post by Kobalt on 2007-03-16
I think you're now ready for the switch then :) 
Two options : you want to keep windows installed and install Ubuntu aside, it's a dual boot. You want to get rid of all of Windows, it's a complete switch. 
Anyways, to guide you through the installation, i suggest you take a look at this : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
It's precise, well described and has screenshots. 

For your backup : do you have a big amount of files you want to save ? How big is that, approximatively ?
Once again, you have many options. A very good option would be, in my opinion, to have a separate /home or /data partition where you'll put all you want to save...

---

### Post by MikeSz on 2007-03-16
Bear in mind that if you're installing windoze, it takes over your hard disk's master boot record so if you want to install windoze at a later date, it will probably kill your ubuntu installation.  The best thing to do is to install windoze on your hard drive, then once everything is working, install ubuntu and give it a decent sized partition.  That way you can dual boot and windoze is always there as a boot option just in case you ever need it.

---

### Post by Kobalt on 2007-03-16
It doesn't actually 'kill your ubuntu installation', just the boot loader Grub, which you can reinstall afterwards from a LiveCD.
Though it's definitely better to install win before Ubuntu, and not the other way around, to spare you the reinstall of Grub...

---

### Post by MikeSz on 2007-03-16
> **Kobalt said:**
> It doesn't actually 'kill your ubuntu installation', just the boot loader Grub, which you can reinstall afterwards from a LiveCD.
Though it's definitely better to install win before Ubuntu, and not the other way around, to spare you the reinstall of Grub...

Fair point but lets not get picky please!  Just trying to keep things simple...

---

### Post by Kobalt on 2007-03-16
Sure :)

---

