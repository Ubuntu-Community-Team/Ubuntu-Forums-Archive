---
title: "Questions re: Partitioning and Repository security"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Monona on 2007-08-22
Hey there.  I just installed Ubuntu on my new laptop (a reconditioned Acer TravelMate 4010).  I don't know much at all about Linux or computers in general (having gone from point and click only to repartitioning my hard drive and installing a new OS in about 3 days), but I'm really excited about learning more about open source software and using it.  Just using the community documentation and wikipedia, I've learned a ton real quickly.

I've got a couple questions, though.  So, here goes:

1. How should I partition my hard drive?

I'll be dual booting my computer into Ubuntu and Windows XP.  I hope to use Ubuntu primarily, but I'm keeping Windows for now.  I will be getting an external hardrive soon.  It would be nice if I could access my files from both Windows and Ubuntu.  

Right now, my harddrive is partitioned into three parts: /dev/sda1 (2.9GB, vfat), /dev/sda2 (26.3GB, vfat, i think this is where my Windows files are), and /dev/sda5 (24.4GB, ext3, this is where ubuntu lives).  I also made a swap space during installation (2000 mb) that doesn't show up in the System Monitor.

How have other people partitioned their drives?  This guide ([http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)) gives a lot of suggestions, but I was a little nervous during setup and didn't want to screw things up.  Would it be better to create a Windows partition, an Ubuntu partition, and a fat32 partition to share data?  How much space should I allocate for each?  Is vfat different than fat32?

2. What makes software repositories secure?

I understand the reasons why open source can be more secure than closed source, but what guarantees that the software repositories are secure?  What's to stop someone from uploading a program that has some kind of harmful function embedded in it?  What kind of risks are there, if any?  Are some repositories more secure than others?

OK, thanks for any help you can offer.  I look forward to participating in the Ubuntu community.

---

### Post by henriette_holm on 2007-08-22
Hi.
I would suggest the following:

Partition1: Windows C: (NTFS or FAT32)

Partition2: Windows D: (FAT32 - use this to share data between win and linux)

Partition3: / (ext3)

Partition4: /home (ext3)

Partition5: swap


Now, if you only have one physical drive you'll have to make an extended partition. Creating a separate /home will allow you to do reinstalls without deleting all you personal files (don't forget a backup though). 

Now, it is possible to install drivers that makes it possible to write to NTFS partitions from linux, as well as write to ext2 partitions from Windows. I have no personal experience with those.

I can't tell you what sizes to use. Learn that from experience. Vfat is the same as fat32.

/Henriette

---

### Post by bodhi.zazen on 2007-08-22
> **Monona said:**
> 2. What makes software repositories secure?

I understand the reasons why open source can be more secure than closed source, but what guarantees that the software repositories are secure?  What's to stop someone from uploading a program that has some kind of harmful function embedded in it?  What kind of risks are there, if any?  Are some repositories more secure than others?

OK, thanks for any help you can offer.  I look forward to participating in the Ubuntu community.

You can follow henriette_holm's advice.

Here is a link for basic Linux partitioning terminology : 

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

=========

In terms of security of the repos, yes stay with the Ubuntu supported repos as much as possible.

FYI : The Ubuntu repos are maintained by the developers and that is who you are trusting to maintain security. The advantage of Open Source is *you* or anyone can download and inspect the source code.

Now I understand most of us are not software engineers but what I am saying is there are thousands of people who are able to watch the code.

You are asking a good question, but, if you think about it, really this is a trust issue. Someone can insert malignant code into either open or closed source. At least with open source the code is available for scrutiny :)

One of the pearls of computer security is ~ Do not install software from untrusted sources. This holds true regardless of OS, open or closed.

---

### Post by Monona on 2007-08-23
Thanks for your help.  I've repartitioned myself a separate /home drive, following your suggestions and also this helpful guide:

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

I repartitioned my drive using GParted and booting from the live CD of Feisty.  I had some trouble until I unmounted my / the terminal and restarted GParted.  Then, it gave me an error message about being unable to mount the drive, but I clicked OK and everything went alright from there.  I remounted and rearranged everything according to the guide mentioned above, and it seems to be working alright.

Thanks again (and to all the other folks having the same problems i did). ;)

---

