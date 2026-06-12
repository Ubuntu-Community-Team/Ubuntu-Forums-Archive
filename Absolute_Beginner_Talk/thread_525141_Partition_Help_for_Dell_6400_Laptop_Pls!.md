---
title: "Partition Help for Dell 6400 Laptop Pls!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by levele304 on 2007-08-14
Hello everyone,

I have recently decided to install Ubuntu 7.04 on a partition to give it a try.  I plan on dual-booting on my Dell laptop 6400(e1505) with Windows XP Home Edition.

I've been reading many forum posts, and while there is alot of useful and insightful information available, i have had trouble finding a complete unified guide.  

In any case, I have a Dell 6400(e1505) laptop with Windows XP installed, and used a modified LIVE CD from [http://www.mylittleubuntuguide.com/]("http://www.mylittleubuntuguide.com/") to make hardware compatibility issues a bit easier.

What I did first was resize my existing windows HD from 70 gigs to 50gigs using the Live CD.

Afterwards, it seems like the CD created 3 new partitions? One called Extended which uses ~25G, another called Linux Ext3 which uses ~22, and a final one called SWAPSPACE2 which uses only 1019,7.  ( I viewed this information with Partition Magic 8, running on XP)

On top of these new partitions, it seems that my DELL laptop came with pre-loaded partitions of its own, most notably a DELL UTILITY FAT partition at the beginning of my disk, along with 2 other small partitions which I havnt the slightest clue what they do or are there for. 

Here is a screenshot of the partitions on my drive to makes things clearer(Partition Magic snapshot): 
 [IMG] http://www.imagedip.com/files/mj4dg3uo4gg5gkozn5yy.jpg[/IMG]


MY question is, which partitions do I need, which ones should i get rid of, and what sizes do you recommend for the ones that I do need?

I also plan on have a NTFS partition to easily share info between Windows XP and Ubuntu (ex. So I can save files from the internet on Ubuntu to a shared drive, which can also be accessed by Windows XP and vice versa)


Any help will be greatly appreciated!

---

### Post by be4truth on 2007-08-14
> **be4truth said:**
> You have XP partitions with NTFS file format
You have an Ubuntu swap partition somewhere with the linux swap file format
You have somewhere at least one linux partition probably with ext3 file system

You might have data partitions either in NTFS or FAT32 or ext3. 
There is software available to read/write linux partitions from Windows [http://www.fs-driver.org/]("http://www.fs-driver.org/") 
I have installed this but don't use it much. I am still a bit worried about the Linux files
You can access NTFS from Ubuntu [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")
Search on this site for NTFS and FAT32 if you want to mount simple FAT32 partitions.
I store my data on FAT32 and Linux and had never any problems.
Come back if you need more help.

for more read this

[http://ubuntuforums.org/showthread.php?t=523445]("http://ubuntuforums.org/showthread.php?t=523445")

---

### Post by levele304 on 2007-08-14
Hey thnx for the link.

However, I am still unsure of what partitions I need.

First of all, judging from the screenshot provided, which partition is my shared drive partition?
The one called 'Extended' or the one called 'Linux Ext3', or is it even in there? If not, what is the extra partition for?  

Please help.  Thanks.

---

### Post by levele304 on 2007-08-14
... any help?

---

### Post by PCFascist on 2007-08-14
For information on the Extended partition go here:
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

Otherwise it seems you have all the partitions you need. (and don't really have any you don't).
If you want I am sure you could delete those that dell put there, but that might require installing windows again... I'm not quite sure.

---

### Post by st33med on 2007-08-14
DON'T DELETE THAT 1st PARTITION! That is necessary for recovery if something goes awry. However, you may want to delete that Local Disk partition with a 'DD Type' type partition. 

But, of course, that may be needed because it is a custom script. I would ask the developer first before getting rid of anything.

---

### Post by be4truth on 2007-08-15
Find attached a how to for partitioning. I am working on it but this is the first draft.

---

