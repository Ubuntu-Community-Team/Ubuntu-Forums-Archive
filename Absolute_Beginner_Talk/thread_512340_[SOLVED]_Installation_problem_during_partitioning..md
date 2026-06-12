---
title: "[SOLVED] Installation problem during partitioning."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by JBrehm on 2007-07-29
Hey everyone,

I've decided to install ubuntu 7.04 (feisty) onto my computer as a dual boot with windows XP media center edition. Everything goes smoothly until I get to "Prepare Disk Space" where it gives me only 2 out of 3 options: 1. Guided. Use entire disk. 2. Manual. Obviously, I want to do a dual boot so I need to be able to partition it for that, and I'm a complete newb to linux and anything past basic computing, so I can't manually partition my HD. Help?

---

### Post by logos34 on 2007-07-29
Either the disk is pretty full or the installer might be detecting blocks of data at the end of the disk--aka in windows-speak 'unmovable' files (those green bands you see in defrag program)--and concluding that it can't resize/shrink it.  Go back into windows and temporarily disable virtual memory/paging files and hibernation, then defrag a couple of times.  Try the install again.

---

### Post by erfahren on 2007-07-29
this standalone freeware app does much better at defragging than the Windows one, although it may take awhile: [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

manual partitioning isn't all that difficult. see this site for thorough instructions with screeshots (I still use it for reference often myself): [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

good luck

---

### Post by JBrehm on 2007-07-29
I have another question. Whenever I boot up with the live disc I get this error message when Ubuntu loads:

[[IMG]http://img253.imageshack.us/img253/1619/screenshotkc2.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshotkc2.png)

Could this possibly have anything to do with the problem I'm having with partitioning my HD? I really want to get ubuntu loaded onto my computer so any help I can get would be great!

---

### Post by wolfen69 on 2007-07-29
that is not an error message. it is simply letting you know that drivers for your wireless card are in use.

---

### Post by erfahren on 2007-07-29
yeah, and it goes away after the first boot and can be gotten to thru System>Administration>Restricted Drivers Manager

---

### Post by JBrehm on 2007-07-29
Well, I feel like a dunce now in regards to the "error" message. Thanks guys.

Ok, so I defragged my system using the jkdefrag erfahren suggested, and it worked wonders! Much better than windows' version (gee, isn't that a surprise). But, unfortunately, it still didn't help to get that third option for dual partitioning. 

logos34, could you explain to me how to temporarily disable those programs you wrote of? I'm not familiar at all with how to do that.

Also, can I repartition my hard drive after I install Ubuntu? I was looking through a site (forget which one) and the writer was talking about several different ways to partition a hard drive, including one way where, if you have a dual-boot, you can have it set up so you have a partition that contains all of your documents and whatnot and it's readable and writable to both windows and ubuntu. Is that something I have to do manually before I install ubuntu, or can I do that afterwards?

EDIT: I found the website where I found the info about the special partitioning. It's psychocats. I'm sure you're all extensively familiar with it.

---

### Post by JBrehm on 2007-07-29
Oh, wait, is it possible that the reason I don't have that option is because my hard drive is NTSF and not Fat32?

---

### Post by erfahren on 2007-07-29
> **JBrehm said:**
> Oh, wait, is it possible that the reason I don't have that option is because my hard drive is NTSF and not Fat32?
that doesn't matter, the partitioner supports ntfs. I did find someone else that had your problem 
[https://answers.launchpad.net/ubuntu/+question/7062](https://answers.launchpad.net/ubuntu/+question/7062)
one of the responses was to make sure you run the Windows check disk, You might want to run it 2 or 3 times. My experience with it on XP is that it doesn't always correct all the errors the first time through. (There is a way to see the log/results of it with the Event Viewer; see the  [Check chkdsk: section here](http://pcworld.about.com/magazine/2405p138id124860.htm)  --- the Administrative Tools can also be accessed thru the Control Panel.) Hopefully that will do the trick. 

about the other partition (a seperate FAT32 to be able to transfer files between the Windows partition and Ubuntu). I use one, but if you can't afford the space for it there is another option. The ntfs-3g driver enables read+write access to the Windows ntfs partition. see [this HowTo](http://ubuntuforums.org/showthread.php?t=217009&highlight=read+write+ntfs). the package is available now thru the Synaptic Package Manager which will get the dependencies you need with it.

you can create and resize your existing partitions using GParted from the Live CD. I don't have much experience with that. It's better to do it beforehand.

About temporarily disabling virtual memory/paging files and hibernation. logos34 meant doing that before runnung the defrag to get better optimization. That may not be neccessary now. this site has instructions for that though: [http://www.smashingboy.blogspot.com/](http://www.smashingboy.blogspot.com/)

---

### Post by JBrehm on 2007-07-29
Well, I've run the check now three times, windows defrag twice, the special defrag suggested to me in this thread, virus/spyware/adware/bad stuff scans, turned off my virtual memory (did the defrags after this), and still there's only two options for partitioning my HD. 

The only other option I can think of as of this moment is for me to try the alternate CD as opposed to the live cd and see if that does anything. If anyone has any other ideas though, PLEASE let me know. Thanks

---

### Post by JBrehm on 2007-07-29
Alright, so I tried the alternate CD, it didn't work. It didn't have any option to partition the drive and use the remaining free space. Help? Please?

---

### Post by JBrehm on 2007-07-29
I've pretty much decided that I'm going to have to manually partition my hard drive so that this will work. My problem is, I think it's been partitioned before, and I don't know what to do with it to manually partition it. When I click "manual" for partitioning my hd, this is what it shows is on it:

SCSI3 (0,0,0) (sda) - 160.0 GB ATA WDC WD1600JS - 75N
           #1 Primary   32.9 MB      K  fat16   /media/sda1
           #2 Primary 155.0 GB  B  K  ntfs      /media/sda2
           #3 Primary     5.0 GB      K  fat32    /media/sda3

Does this help at all with knowing what to do? I really could use some help. I've never done this before.

---

### Post by logos34 on 2007-07-29
oh, no wonder you're having problems--you have a couple of utility/recovery partitions in addition to windows--the installer wants to create create two extra paritions for / (root) and /swap (either both primaries or the latter inside an extended partition) but can't because your can only have a max of 4 primaries or three + 1 extended.  

You'll have to manually create an extended partition out of the space freed up after shrinking windows, then you create / and /swap (and a separate /home if you want) inside as logical partitions.

---

### Post by JBrehm on 2007-07-30
logos, thank you very much for your help! Unfortunately, I'm not totally sure how to do what youve said to do. I've already gone in through the alternate cd and resized the windows partition from 155gb to 54gb and have 101 gb free space. now how do i do what you wrote of?

EDIT: oh, also, do you happen to know what the other two primary partitions are for exactly? would you happen to know what would happen if i were to delete the smaller of the two, or change it to a logical as opposed to primary?

---

### Post by logos34 on 2007-07-30
simply choose the unallocated/freed space and create a type = extended partition for all of it.  Then make two logicals inside - ~512 MB - 1 GB swap (type swap)  mounting at '/swap' and the rest to root (type ext3) with mount point '/'.  Or you could give say 7-10 GB to / and the rest to a separate /home (ext3).  That way if you ever have to reinstall your data and settings files will remain untouched.

edit: here's a good dual-boot howto using the alternate cd that should help you out
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by JBrehm on 2007-07-30
i'm sorry to have to ask such a stupid question and waste your time, but i'm thoroughly confused as to how exactly you create a type = extended partition. i tried several times, using both the alternate and live cds (i'm now curently using the live disc) and i see no option for making it into an extended partition. how do you do that?

and i think you may have missed my other question: what would happen if i were to delete one of the other primary partitions or to change one from primary to logical (or would that even do anything in regards to allowing me to create all of the partitions i need?)?

---

### Post by logos34 on 2007-07-30
You could delete one of the utility partitions, but I refrain from suggesting that...you might need it later. It's up to you.

As I said here or somewhere else, I've been through the install countless times (live and alternate cd) and for the life of me can't keep a mental picture of each and every step.  To make an extended on the live cd I know you can just go to system>admin>gnome partition editor and use that to create it, then go through the manual steps to set up root and swap as logical partitions inside the extended.

---

### Post by logos34 on 2007-07-30
ok, I just checked the live cd, and for manual partition it seems to only give you a choice of filesystem type (ext2, ext3, swap, etc) and mount point--[see this]("http://img264.imageshack.us/my.php?image=feistydual12xc2.png")...it doesn't indicate whether the partition is a primary or logical.  But just use gparted to create the extended and then run through manual install and make / and swap.  Or use the alternate cd.  I've use mostly the alternate to install root on logical partitions all the time.  (Just tried out Gutsy x64 the other day).

---

### Post by JBrehm on 2007-07-30
Thanks logos, you've been a great help! I made that free space extended and root partition and swap partition out of it (figure I can organize it all so i have a /home partition and a fat32 partition later on with gparted). I then went on to use the automated partitioner (figured it'd be safer, and i can always fix it all in the end if it gets messed up) and it's installing as i speak (er... type). I'll let you know how it goes!

---

