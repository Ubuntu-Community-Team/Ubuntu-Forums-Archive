---
title: "n00b - Dual Boot XP Prof with Ubuntu"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-30
Hey all,
I'm a noob at linux, and trying it out for the first time. As much as I am excited, I am a little concerned about the whole process. I was reading the documentation and a few ebooks on Ubuntu. Anyway, coming down to the point, Ubuntu requires a RAW partition, and i presently have two partitions on my hdd.

C: 30 GB (FAT32) - Windows Drive
D: 210 GB (NTFS) - Data Storage

So right now, I'm on XP, I was planning to abandon XP totally and move to linux, but I think I need more exposure to linux before i can phase out xp. Anyway, so then came my idea to dual boot. 

So I wanted to get a few things clear. Here is what I plan to do, and guide me if I'm wrong anywhere.

Create RAW Unformatted 10-20 GB Partition with partition magic in windows.
Boot with Ubuntu Disc
Install Ubuntu on New Drive.

Does ubuntu give me an option on which drive i want to install it on? 
Plus will I be able to select the OS I want to boot from at start up?

Sorry, but I'm a total n00b, so really need some help.
Thanks in advance,
Sibot

---

### Post by sankarv on 2007-05-30
there is no need for you to even create partition with partition magic since ubuntu does it all for u.

[B]backup your system data if necessary .
[/B]

just boot the ubuntu cd and it will ask u series of questions an then comes to perform partitioning (auto /manual ).

auto will erase entire harddisk. select carefully manual partitioing option.

u can create new partitions if you have free space or remove existing partition and create new ones. removal of existing ones will result in loss of data from that partition.  do this carefully.



if you have another os installed ubuntu will auto detect at the time of installking its boot loader grub and after installation when u r rebooting it will provide options for which os to boot.





read this link before install. it has links to installation and other things. it will help you more.


[http://ubuntuforums.org/showthread.php?t=232059]("http://ubuntuforums.org/showthread.php?t=232059")

---

### Post by sibot on 2007-05-30
Thanks! one more question would the linux installer detect my NTFS partition?

---

### Post by Atomic Dog on 2007-05-30
If the space is unpartitioned the installer will allow you to choose the "empty" space to install Ubuntu.  That's how I always do my installs.  I shrink a partition to a size I desire, then let Ubunti use the blank space to install itself.

---

### Post by zvacet on 2007-05-30
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by sankarv on 2007-05-30
yes its detecting ntfs partitions  for me....

---

### Post by sibot on 2007-05-30
hmmm yeah i think ill go about it that way too atomic dog, create a RAW partition with partition magic and let ubuntu installer install there. Whats the whole deal with the swap partition? does it have to be manually created or the installer makes it?

---

### Post by drowner on 2007-05-30
> **sibot said:**
> hmmm yeah i think ill go about it that way too atomic dog, create a RAW partition with partition magic and let ubuntu installer install there. Whats the whole deal with the swap partition? does it have to be manually created or the installer makes it?

If you choose the manual partition, you have to make it yourself, otherwise it will do it for you, if you choose a guided partition.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by sibot on 2007-05-30
thanks for the link, I read the matter. I have one question, say I create a RAW Partition out of my free space in D: (NTFS) (Data Drive) and I want to install ubuntu on that, plus create the swap space out of that provided space only. Is it possible? Correct me if I'm wrong; I'll have to choose manual installation, and choose the unformatted space?

---

### Post by sibot on 2007-05-30
sorry for all the fuss, but i have around 150 gb of data on my hdd which i cannot afford to lose, so i need to be extra extra sure what im going to be doing while installing ubuntu. I'm thinking of keeping another computer alongside and taking help from the IRC Chat alongside.

---

### Post by hellmet on 2007-05-30
If you're more comfortable creating partitions on Windows , then I'd suggest you create one partition with space enough for ubuntu, and another one with space atleast as much as your RAM.
Then boot ubuntu cd. Assign the first partition as ext3 and mount it on / and assign the second as SWAP. 
Thats all.

---

### Post by drowner on 2007-05-30
> **sibot said:**
> thanks for the link, I read the matter. I have one question, say I create a RAW Partition out of my free space in D: (NTFS) (Data Drive) and I want to install ubuntu on that, plus create the swap space out of that provided space only. Is it possible? Correct me if I'm wrong; I'll have to choose manual installation, and choose the unformatted space?

My personal preference, would be to

1. Backup

2. Use a manual install, but only because I am more familiar with the manual install. I have done it several times, and had never had any trouble with damaging files, but you should still back up, and defragment before commencing.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

has an excellent walk through of the manual installation, using the liveCD

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) has an excellent walkthrough of a manual partition using the AlternateCd (text based, my preference, as i have an older system.)

Provided C: and D: are two partitions of the same drive, i don't foresee any problems.

---

### Post by sibot on 2007-05-30
ah alright..thanks...so i have 1 gb ram, so ill make a 2gb swap partition and a 15gb one for ubuntu...thanks all!

---

### Post by bmagyarkuti on 2007-05-30
You can also choose to resize one of your exsisting partitions to get free space from the ubuntu install partitioner (gparted, practically). Yet, it is a little risky :)

---

### Post by sibot on 2007-05-30
@drowner, thanks for the help, i looked through the site, and it is indeed pretty helpful! thanks!

---

### Post by sibot on 2007-05-30
ext3? can i name it anything? or i have to name it ext3?

---

### Post by drowner on 2007-05-30
> **sibot said:**
> ext3? can i name it anything? or i have to name it ext3?

What do you mean?

ext3 is not the name of the drive, its the filesystem, like FAT32 or ntfs

---

### Post by sibot on 2007-05-30
oh k...lol :P thanks..i think i'm ready to install ubuntu then! =D thanks all!

---

### Post by ukripper on 2007-06-06
I have created seperate /home partition and linked it with / just as a part of backup plan.

---

### Post by claytor on 2007-06-06
I too am installing linux for the first time (finally!!!).

I have just installed ubuntu studio 7.03.  I already had xp pro installed on a 15gb partition, had 40 gb NTFS formatted (for non-system files), and left the rest of my drive untouched (about 60gb).  I popped in the ubuntu disc, and installed it on the 60gb partition.  

It acknowledged my XP os, and the grub boot loader worked the first time I tried it.  With a modem restart and a few updates, everything seems to be working fab.  Didn't even have a prob mounting and accessing files off my 40gb NTFS partition.

This is my first post here, and am looking forward to many sleepless nights getting to know my linux...

Thanks in advance to the entire community!!!

---

### Post by ukripper on 2007-06-06
> **claytor said:**
> I too am installing linux for the first time (finally!!!).

I have just installed ubuntu studio 7.03.  I already had xp pro installed on a 15gb partition, had 40 gb NTFS formatted (for non-system files), and left the rest of my drive untouched (about 60gb).  I popped in the ubuntu disc, and installed it on the 60gb partition.  

It acknowledged my XP os, and the grub boot loader worked the first time I tried it.  With a modem restart and a few updates, everything seems to be working fab.  Didn't even have a prob mounting and accessing files off my 40gb NTFS partition.

This is my first post here, and am looking forward to many sleepless nights getting to know my linux...

Thanks in advance to the entire community!!!

Goodluck in your first step and hope you would enjoy to be a part of large Family in the world.:popcorn:

---

