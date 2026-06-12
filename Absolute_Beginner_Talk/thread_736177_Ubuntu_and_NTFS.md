---
title: "Ubuntu and NTFS"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by broken sword on 2008-03-26
Hello, I am working on dual booting between linux and windows.  After some issues, I had to completely wipe my system and start over (should have done it in the first place).  I have a 200 GB drive, which is broken up in the following way:

40 GB for Vista
100 GB (flexible) Shared Data
1 GB Swap (?)

I readthat 20 GB is good enough for Linu, is this true?

Also, the main question, can Linux read NTFS partitions natively?  I know that I have to use Vista to create the partitions, I would prefer NTFS, but will unsure if Ubuntu can read it.

---

### Post by nitro_n2o on 2008-03-26
20 GB should work, but more disk and more ram are always good :) 

generally your swap space should be double your ram size, more info on tldp

as for ntfs just do 
sudo apt-get install ntfs-3g

Don't install the system on NTFS.. this is a bad idea and you don't need Vista to partition your disk, you can do this from the live CD of ubuntu, but make sure you isolate the vista partition from inside vista before you do the partitioning in ubuntu 
check out google for dual booting ubuntu

---

### Post by pedro_orange on 2008-03-26
Yes Ubuntu can read NTFS File systems, even though it is not native Linux file system.

Smashing guide: [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by broken sword on 2008-03-26
I just want the shared data drive to be ntfs, wouldn't install ubuntu on ntfs.

I did some research, and one place said it was best to let vista do the partitioning.  I used gparted and the live cd to partition, and ran into problems.

Also, I have 4 GB of RAM, do I really need 8 GB swap?

And as far as Ubuntu reading NTFS, are there any issues concerining that? I would like to keep movies and music and documents on there, w/o having to worry about them being corrupted.

---

### Post by tombott on 2008-03-26
Last time I dual booted with Vista (actually the only time), I let Vista partition the disk on install.
I then used the Ubuntu Live CD, resized the partition and used free space to create ext3 and NTFS partitions.
This all worked without any problems.

---

### Post by Boyohazard on 2008-03-26
The problem as I understand it isn't the reading, its the writing. Hence the recommendation to install ntfs-3g

---

### Post by oedha on 2008-03-26
> **broken sword said:**
> I just want the shared data drive to be ntfs, wouldn't install ubuntu on ntfs.

I did some research, and one place said it was best to let vista do the partitioning.  I used gparted and the live cd to partition, and ran into problems.

Also, I have 4 GB of RAM, do I really need 8 GB swap?

And as far as Ubuntu reading NTFS, are there any issues concerining that? I would like to keep movies and music and documents on there, w/o having to worry about them being corrupted.

yes...you can make one big ntfs as winlin data partition
about swap.....no need to be 8....make it 2.......and your RAM is too much :)
about gparted.......which gparted.......have you try gparted liveCD :==> [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by ace007 on 2008-03-26
20 GB for a linux partition is monstrous.  If you plan on keeping all your documents, pictures, etc on the shared partition, then 10 GB is plenty for a Linux partition.  I've got a full blown installation of Gutsy running fine on 6 GB of space.  Also, a windows Partition shouldn't have to be bigger than 20 GB either.  Unless you plan on installing more than a few bloated programs, 20 GB should be fine for windows.

---

### Post by trashie on 2008-03-26
Hi there,

If  you want to have a shared partition between Windows and Linux, I advise you to use ext3 filesystem.

There is several reason for that :
* very well managed by Linux and much more powerful than NTFS
* you can read/write  on it under Windows via this [driver]("http://www.fs-driver.org/") , loosing the advantage of journal, but it is safe, stable and transparent

Many people will tell you that there are some risks, but by my own experience I never noticed any problem, contrary to the use of NTFS... But to be honest, here are some risks :
* if your root partition is in EXT3 under Linux, then it is possible under Windows (if this partition is mounted) to modify, regardless the permissions, any file. But no  problem if you do not mount it (AS STRONGLY RECOMMENDED)
* as said before the journal is not used under Windows, but it is used under Linux, and then it is just like and EXT2 partition under Windows.

If you still want to use NTFS partition, use ntfs-3g driver as suggested above, but use the driver from the website, since the one in repository is outdated and may lead to some problems...

good luck,

Mathieu

---

### Post by stchman on 2008-03-26
> **broken sword said:**
> Hello, I am working on dual booting between linux and windows.  After some issues, I had to completely wipe my system and start over (should have done it in the first place).  I have a 200 GB drive, which is broken up in the following way:

40 GB for Vista
100 GB (flexible) Shared Data
1 GB Swap (?)

I readthat 20 GB is good enough for Linu, is this true?

Also, the main question, can Linux read NTFS partitions natively?  I know that I have to use Vista to create the partitions, I would prefer NTFS, but will unsure if Ubuntu can read it.

Yes Ubuntu can READ NTFS OOB.  If you want to be able to write to NTFS partitions you will need to install the ntfs-3g package.  I have tutorial on partition mounting in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

I have been using ntfs-3g for some time and no problems.

---

### Post by forrestcupp on 2008-03-26
Ubuntu now has the ntfs-3g package installed by default.  You can read *and* write to an NTFS partition out of the box in Gutsy.

I would definitely use NTFS for your shared partition for 2 reasons.  1 - Linux does NTFS better than Windows does ext3.   2 - If you make Windows do ext3, you'll be able to screw up your Ubuntu install easily.

And about 20 GB for Linux, it depends on what you are going to be doing.  If you are storing your videos on the shared partition and that's all you're going to be doing, then of course 20 GB is enough.  But it's just like Windows.  If you're going to install a lot of programs and games, they have to go somewhere, and it's just as easy to fill up 20 GB with apps/games in Linux as it is in Windows.

---

### Post by TechJuice on 2008-03-26
I wrote a guide on partitioning this way with XP and Ubuntu. It worked pretty well for me, and I really enjoyed having that shared partition. I'm not sure if Vista would cause a real difference, but go ahead and check out [http://www.thetechjuice.com/2007/10/ultimate-dual-boot-ubuntu-gutsy-windows.html](http://www.thetechjuice.com/2007/10/ultimate-dual-boot-ubuntu-gutsy-windows.html)

I'm not sure what the rules are as far as posting my own site as a reference, but if it is looked down upon I apologize. Just trying to help.

Let me know how it goes for you.

Edit: Actually my guide is for a shared ext3 partition, which was better in my opinion.

---

### Post by broken sword on 2008-03-26
When partitioning my hard drive, my shared data drive (/home mount for ubuntu), should it be primary or logical?

---

