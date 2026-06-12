---
title: "Switching from WinXP to Ubuntu. Linux newbie questions inside!"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Swipe on 2006-09-20
Hello,

Recently, I decided to give Linux a try. So after a bit of research and a few recommendations I have picked Ubuntu as my first distro. Mainly because it is praised as newbie-friendly - a quality that is going to be oh-so-useful in my case. :)

I've played around with the LiveCD a bit and I have to say that I'm happy with what I saw. However. I have a few questions before I install it and start messing around with it (<- something I'm really looking forward to). 

Two that bug me the most are:

1. Is it OK to use a 32bit kernel if my system is built around a AMD64 dualcore CPU? I've heard that the 64bit support is a bit scatchy all around.

2. What would be the easiest way to migrate data from Windows? Short of burning it all on a couple of DVDs, creating a partition (FAT32) that both Windows and Linux can read/write to seems like an option from what I've read. This could also be useful, since it is obvious that I will not be able to switch instantly and both OSes are going to be in use for quite some time. Is it easy to do? Are there any other solutions?


Thanks!

---

### Post by nir78 on 2006-09-20
Hi Swipe,

I was in your position 6 month ago and since than I use only Ubuntu - It's is for sure a lot better !! :razz: 
Regarding your q's:
1. Yes, you can install the 32bit on AMD 64bit - I am doing it myself too as I found out that the 64bit does support all applications.

2. I found that the best way to migrate and "leave the door open" for returning at any time is to create a new FAT32 partition with access from any operation system.

Hope this will help you and good luck!
Nir

---

### Post by kipeloff on 2006-09-20
Hello,

1) There is no problem. I'm using 32-bit Ubuntu on the 64bit workstation. Ubuntu works without any problem. You can search for the topics, where discussed the difference between 32 and 64 distributions.
The main idea is to use 32 for the home PC as far as I understand.

2) Burning DVD will be the most safe option to move your data ;) 
you can use dual boot to run programs, that are not executable under Ubuntu.

---

### Post by jd65pl on 2006-09-20
Did you read the sticky thread on naming threads? Please give your thread a more informative title if only for the benefit of other people with similar questions.

perhaps
> 32bit kernel on AMD64 & sharing data between two OSes?

Click [here ]("http://www.ubuntuforums.org/showthread.php?t=260731")for the thread

---

### Post by Najand on 2006-09-20
Well, it supports 32 bit completely, but if you want not to experience slow system, better to start AMD64 version.

---

### Post by Swipe on 2006-09-20
Aha!

That's what I needed to know! 

Are there any good HOWTOs on creating and sharing a FAT32 partition across multiple OS?


Thanks again!

---

### Post by Swipe on 2006-09-20
> **jd65pl said:**
> Did you read the sticky thread on naming threads? Please give your thread a more informative title if only for the benefit of other people with similar questions.

perhaps


Click [here ]("http://www.ubuntuforums.org/showthread.php?t=260731")for the thread


Sorry about that. I'll try to be more precise with the thread titles in the future.

---

### Post by missmoondog on 2006-09-20
> **Najand said:**
> Well, it supports 32 bit completely, but if you want not to experience slow system, better to start AMD64 version.

don't know what would be slow about that persons system running 32bit on a 64bit machine? it obviously has to be new enough to have enough horsepower to make up for it. besides, as already stated, 64bit is still slightly buggy.

---

### Post by Najand on 2006-09-20
As far as I know, installing two or more different systems on a partition is impossible, but if you want you can resize one partition to decrease its size, then make a new partition on free space made after resizing. (Defragment of your "Windows" partition and enough free space is needed in order to  repartition "Windows" partitions. The default partitioner that is used in ubuntu is "gparted" which has very easy to use/understand interface and it is not very difficult to use it... Takw a look at its site to get familiar with it... Also for installing linux, it is strongly recommended to  use "ext3" filesystems instead of "fat32", "ex2" or any other filesystems.

---

### Post by jd65pl on 2006-09-20
You can edit the thread title by clicking on the scissors on your original post.

In terms of your shared partition you will need to create a new fat32 partition separate from your ubuntu install.

Then see this link on how to utilise your partition
[http://www.ubuntuforums.org/showthread.php?t=257602&highlight=fat32+windows+share]("http://www.ubuntuforums.org/showthread.php?t=257602&highlight=fat32+windows+share")


Edit:
You may also find this link useful whenyou have made your fat32 partition
[http://www.ubuntuforums.org/showthread.php?t=257472&highlight=fat32+windows+share]("http://www.ubuntuforums.org/showthread.php?t=257472&highlight=fat32+windows+share")

---

### Post by jd65pl on 2006-09-20
Here is a how to i found using the power of google ;)

[http://www.geocities.com/epark/linux/partition-share-HOWTO.html]("http://www.geocities.com/epark/linux/partition-share-HOWTO.html")

---

### Post by Swipe on 2006-09-20
> **jd65pl said:**
> Here is a how to i found using the power of google ;)

[http://www.geocities.com/epark/linux/partition-share-HOWTO.html]("http://www.geocities.com/epark/linux/partition-share-HOWTO.html")


Ah. That's gonna help once I get that far.

Editing the "Title" field, however, doesn't seem to work. It edits only the title of the initial **post** not the entire thread.

Maybe I'm missing something? :confused:

---

### Post by jd65pl on 2006-09-20
Ah never mind perhaps one of the admins will change it at some point. I think the world will probably still turn (i hope)

J

---

### Post by jbennet on 2006-09-20
a 4ghz 64 bit cpu will run the same as a 4ghz 32 bit cpu if you use the same os.

However, if the 64 but cpu has a 64 bit os it will be faster

Use the 32 bit version as this extra speed isnt importnat unless for games/development/server. the 32 bit version is much more stable and has more apps too

---

### Post by crokett on 2006-09-20
> **Swipe said:**
> Hello,
2. What would be the easiest way to migrate data from Windows? Short of burning it all on a couple of DVDs, creating a partition (FAT32) that both Windows and Linux can read/write to seems like an option from what I've read. This could also be useful, since it is obvious that I will not be able to switch instantly and both OSes are going to be in use for quite some time. Is it easy to do? Are there any other solutions?


Thanks!

Why do you need a FAT partition? If you are nervous about losing data or have to rework the HDD to get a partition to put Ubuntu on, then you need to back up your data.  But if you only want to read the windows partitions,jJust install Ubuntu. I am dual booting Windows XP and Ubuntu and it is fat and happy mounting and reading my NTFS partitions quite nicely.

---

