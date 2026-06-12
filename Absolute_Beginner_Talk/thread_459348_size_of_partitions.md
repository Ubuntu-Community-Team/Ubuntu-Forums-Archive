---
title: "size of partitions"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by dathascome on 2007-05-30
Hi there. This is my first time installing linux and I've been reading up on it for a little bit and think I'm set to do it.  I decided I'm going to dual boot. If I understand correctly I can use fs drive to read/write from XP onto EXT2. So I can shrink my XP NTFS partition, and create a / partition for ubuntu and /home as EXT2 and then a swap partition. 
So my question then is I have an 80gb hd and a 320 gb external drive (i can use NTFS-3G to write onto the external drive right?), I want to put ubuntu and XP on the 80gb hd, but I'm not sure how much space to allot to each partition eg: the XP, Ubuntu, swap, and /home (which they will share). I'm also unsure of exactly what files go into the / partitions for XP and Ubuntu and what goes into the /home. Is it just system files that go into each OS's respective / partition and everything else goes into the /home? 
I'm guessing that I'd want to make the Ubuntu and XP partitions as small as I can and leave the rest of the space for the /home they will share right?
I just have no idea what's an adequate size (out of 80gb) for the Ubuntu and XP partitions.
Any help would be greatly appreciated

---

### Post by kernel tom on 2007-05-30
well if you wanted to you can devote most of your partions to that "other" OS

Ubuntu can acutally be loaded and ran from a flash drive, so rumor has it, especially if you are saving all your data to ur external.

I'd give yourself 20 gigs for ubuntu just so u have the option of saving files to your home directory before moving them to ur ntfs drive

Caution: NTFS-3g is undoubtabley an amazing tool, but if your life depends on ur files then you won't want to rely on it 100%.  FAT32 formatting is a bit slower, but can be read/written by linux and windows alike

EDIT:::
more closely something like this
20 gigs for your sda1 (linux)
1.5 gigs for your sda2 (extended)
1.5 gigs for your sda5 (Iinux swap / solaris)

*sda could be hda depending on what version ur using, but u get the idea?

---

### Post by az on 2007-05-30
> **dathascome said:**
> 
I'm guessing that I'd want to make the Ubuntu and XP partitions as small as I can and leave the rest of the space for the /home they will share right?
I just have no idea what's an adequate size (out of 80gb) for the Ubuntu and XP partitions.
Any help would be greatly appreciated

It depends.

You shouldn't have to worry about what files go where.  Whether your home is on a separate partition or not, you don't really have to deal with that.  You don't want to make any of your partitions too small, since it is a pain to resize them afterwards.  

By far, the simplest and safest procedure is to just take the default (automatic) partitioning scheme - all on one partition plus swap.  You are in possession of a large external drive so that if you ever had to backup your home drive, it is trivially easy.  You do not need a separate home partition.

---

### Post by Inxsible on 2007-05-30
> **dathascome said:**
> Hi there. This is my first time installing linux and I've been reading up on it for a little bit and think I'm set to do it. I decided I'm going to dual boot. If I understand correctly I can use fs drive to read/write from XP onto EXT2. So I can shrink my XP NTFS partition, and create a / partition for ubuntu and /home as EXT2 and then a swap partition. 
So my question then is I have an 80gb hd and a 320 gb external drive (i can use NTFS-3G to write onto the external drive right?), I want to put ubuntu and XP on the 80gb hd, but I'm not sure how much space to allot to each partition eg: the XP, Ubuntu, swap, and /home (which they will share). I'm also unsure of exactly what files go into the / partitions for XP and Ubuntu and what goes into the /home. Is it just system files that go into each OS's respective / partition and everything else goes into the /home? 
I'm guessing that I'd want to make the Ubuntu and XP partitions as small as I can and leave the rest of the space for the /home they will share right?
I just have no idea what's an adequate size (out of 80gb) for the Ubuntu and XP partitions.
Any help would be greatly appreciated
 
I guess you are bit confused in the concept of / (root) and /home.
 
Windows XP has nothing to do with either of those. / (root) is where your Ubuntu OS lies. /home is where your Ubuntu users will have their personal space -- Something like Documents and settings in XP where all users in XP have their folders.
 
There are ways to have your /home be shared in XP so you can transfer files between the two partitions but dont confuse that with XP sharing the /home drive.
 
About your drive sizes,
 
If you use or will use XP a lot and you have bloated apps like AutoCAD or huge games then you might have to judge the space yourself
 
This is what I did with mine: Total 160 GB
25 GB Windows OS
25 GB Windows Data (including games and software installation)
72 GB /shared (EXT3 partition) -- my music and movies and photos -- i share ONLY this partition in Windows Vista
/ (root) 9 GB -- Ubuntu OS
/home 20 GB -- Ubuntu Os home partition -- I do not allow XP to touch this. I dont want XP to mess around with my Ubuntu installation AT ALL !!!
swap - 1 GB -- Ubuntu swap
 
Although I let Ubuntu access both my Windows drives ;)
 
You see, I am partial to Ubuntu

---

### Post by dathascome on 2007-05-30
Thanks for all the replies. 

They sort of clear things up, but also bring up more questions if i may. I have all of my movies music etc on my external drive right now so that the only thing on the 80gb hd is the windows OS and various programs. Before I install Ubuntu, I defrag a bunch of times to make the drive more contiguous and force everything to one side as much as I can. So then when I shrink my current XP partition and try to partition it will know to not cut into a spot where my windows files are already? What about unmovable files?

Also, is it a good idea to separate the partition where I keep windows OS and any windows program files (similar to what Inxsible had mentioned) ? 

Inxsible, your Ubuntu /home partition is analogous to your windows data partition then, but for their respective OS?

Perhaps this is a silly question but what exactly is the purpose of a /home partition? From what I've read it seems that it's more of a precaution in case one needs to reinstall Ubuntu or something. But otherwise, as az suggested, I perhaps don't need one if I have a large external drive that I can use for backing up, correct?

Is it true that if I already have 1gb ram that I don't need a /swap?

Last question, Kernel Tom, you suggested >  1.5 gigs for your sda2 (extended)
what is extended?

Thanks again for the help

---

### Post by Inxsible on 2007-05-31
> **dathascome said:**
> Thanks for all the replies. 

They sort of clear things up, but also bring up more questions if i may. I have all of my movies music etc on my external drive right now so that the only thing on the 80gb hd is the windows OS and various programs. Before I install Ubuntu, I defrag a bunch of times to make the drive more contiguous and force everything to one side as much as I can. So then when I shrink my current XP partition and try to partition it will know to not cut into a spot where my windows files are already? What about unmovable files?

Also, is it a good idea to separate the partition where I keep windows OS and any windows program files (similar to what Inxsible had mentioned) ? 

Inxsible, your Ubuntu /home partition is analogous to your windows data partition then, but for their respective OS?

Perhaps this is a silly question but what exactly is the purpose of a /home partition? From what I've read it seems that it's more of a precaution in case one needs to reinstall Ubuntu or something. But otherwise, as az suggested, I perhaps don't need one if I have a large external drive that I can use for backing up, correct?

Is it true that if I already have 1gb ram that I don't need a /swap?

Last question, Kernel Tom, you suggested 
what is extended?

Thanks again for the help

/home is where all my user settings will be stored. The purpose of having a separate /home is that when the next release of Ubuntu comes in, I can do a fresh install of it in my / (root) folder and keep the /home untouched. That way i won't have to redo all my settings again.

You would still need a swap partition. I have 2 GB RAM, so i just have a 1GB swap partition. Generally, ppl keep 1.5 -2 times the size of RAM. but i think when you have 2GB RAM, your swap hardly gets used !

I have never seen my swap getting used more than 33 % in the last few months that i have been using Ubuntu. I have a system monitor which i keep checking to see the usage.

---

### Post by dathascome on 2007-05-31
I think that part of my confusion is from using windows perhaps. Right now with windows I just have one  large partition and both the OS and and settings are there and when I change a setting it of course goes in the single partition along with the OS, but with Ubuntu I can have just the Os in the / (root) folder and have a separate one for settings right?  
So then if i set up the / (root) folder and a /home folder when actually using Ubuntu it will automatically save whatever settings I have in the home folder?

---

### Post by kernel tom on 2007-05-31
> **dathascome said:**
> Thanks for all the replies. 

Last question, Kernel Tom, you suggested 
what is extended?

Thanks again for the help

wiki has some good information on types of partitions, i'd go here to answer that question
[http://en.wikipedia.org/wiki/Partition_(computing)#Extended](http://en.wikipedia.org/wiki/Partition_(computing)#Extended)

hope it helps

---

### Post by dathascome on 2007-05-31
Great, I'll check it out, thanks:D

---

### Post by az on 2007-05-31
> **dathascome said:**
>  So then when I shrink my current XP partition and try to partition it will know to not cut into a spot where my windows files are already? What about unmovable files?

The partitioning software on the Ubuntu install disk will take care of that for you.  It will not blindly write to the disk.  It can mode data around.  However, if there is the slightest doubt about data loss, it will refuse to do anything.  In that case, you often will be successful by using the windows defragmenter -  that will move things around and make it easier for the Ubuntu installer to partition.


> **dathascome said:**
>  
Also, is it a good idea to separate the partition where I keep windows OS and any windows program files (similar to what Inxsible had mentioned) ?  

No.  Windows only uses one partition.  When you install apps in windows, it writes to the registry.  If you want to reuse that partition, you will still need the registry entries (which will not exist on your re-installed version of windows)


> **dathascome said:**
>  
Is it true that if I already have 1gb ram that I don't need a /swap?

No.  You need a swap.  You will probably use it less, but it will make your system a lot more stable if, even occasionaly, you use a lot of ram.  But who cares?  The installer will create a swap partition for you when you install (unless, of course, you pick manual partitioning and then don't create one manualy!)

> **dathascome said:**
> 
So then if i set up the / (root) folder and a /home folder when actually using Ubuntu it will automatically save whatever settings I have in the home folder?


Not really.  There are system setting in the /etc which is on /.  There are also settings in /var/lib.  So, there is no easy way to preserve your settings.  What is in /home is only your user settings.  Often enough, when you bork your system, you will need to get rid of those settings anyway!

However, if you avoid third-party apps, it is ridiculously easy to upgrade from one release to the next.  I strongly emphasize upgrading over re-installing.

If you ever bork your desktop and are thinking about reinstalling, create a new user and log into that accout to see if that fixes everything....

---

### Post by dathascome on 2007-06-01
Ok, this is my last question before doing the deed. As for the partitions what I will do is shrink my windows partition, create a swap file, create the /(root) partition and lastly I want to create an EXT3 partition that both ubuntu and windows can read and write onto (using fs-drive  for windows). Is there anything special I need to do to do this? Like I can just make it the /home partition and then both will be able to use it with no problems?

Thanks again all, next time I write back will be from ubuntu hopefully;)

---

