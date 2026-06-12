---
title: "Please give installation advice to a newbie"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-14
Hey everyone.  I've been a lifelong Windows user and have always thought about trying to make the switch to Linux but have never taken the time or effort to get it done.  Now I've finally decided to go with Ubuntu.  Basically, I want to install Linux along side Windows XP as a dual-boot system.  I'd rather keep Windows as is and install Ubuntu in order to learn the Linux system and then eventually one day just use linux as my main OS.

Here's what I've got:

1 40GB NTFS hard drive that has Windows XP installed on it
1 250GB NTFS hard drive that is brand new and has nothing on it

What I'd like to do is leave the first hard drive as is, then take the second hard drive, partition off part of it for linux, then use the rest of it as shared space between the two operating systems.

I've been researching exactly how to set my system up like this, and have read multiple guides, but am having trouble piecing everything together.  If there would be anyone kind enough out there to answer my questions and kind of take me through step by step, I would really really appreciate it.

1. If I use a program like Partition Magic to partition off 20 GB at the beginning of my 2nd hard drive (hdb), that should be plenty for Ubuntu right?

2. After my partition is ready and I start the installation process, I understand I'll have to make a couple of other partitions for Linux: /root and /swap.  How much should I make each partition?

3. How do I get the boot loader to work and is there anything special I need to do during install?  I read that the best method may be to configure Windows boot loader (NTLDR) to hand off to the GRUB boot loader on hdb that will load linux, but I have no idea how to do this really.

My main concerns are really just making the partitions, what size the partitions should be, and how to ensure that I can share the remaining space on hdb between both Linux and Windows.  My second concern is getting the boot loader to work correctly.  Besides that, I believe I can do the rest of the install myself.

I know this is long, but thanks for reading and if anyone can offer advice to a newbie, I would be really grateful.

---

### Post by Sef on 2006-05-14
> 1. If I use a program like Partition Magic to partition off 20 GB at the beginning of my 2nd hard drive (hdb), that should be plenty for Ubuntu right?


Don't use PM, it and linux don't always get along real well.   There is a partitioner in the install.  If you want to use a commercial one system commander works real well.

> 2. After my partition is ready and I start the installation process, I understand I'll have to make a couple of other partitions for Linux: /root and /swap. How much should I make each partition?


for linux make 3 partitions:

root, swap, and home

Also you may want to make another one of FAT32, to share files with XP.

> 3. How do I get the boot loader to work and is there anything special I need to do during install? I read that the best method may be to configure Windows boot loader (NTLDR) to hand off to the GRUB boot loader on hdb that will load linux, but I have no idea how to do this really.

Grub should automatically pick up both.  Ubuntu will be your default, and windows will be an option.

---

### Post by stevenash on 2006-05-14
Thanks for the quick reply Self!

I will use the partitioner in the install then to make all the partitions.

Will making a 20 GB NTFS partition be enough for linux?

How much should should the /swap /home /root partitions be?

So GRUB will work fine, even if Ubuntu is installed on a completely different HD?

Thanks again.

---

### Post by Kvark on 2006-05-14
You'll need these 4 partitions on the second disk:
swap: at least equal to your ram.
root: at least 5 GB (yes, seriously, I have installed a LOT of programs and it still only takes 3.6GB for me, but why not make it 20GB, maybe you'll install Unreal Tournament 2004 or something else thats really big)
home: as much as you want for files that you will only use in Linux.
D: as much as you want for files that you will share between Windows and Linux.

Root and home should use the filesystem "ext3", swap should use "memory swap" or something and D: should use "FAT32".

And yes grub will work fine.

---

### Post by Bartender on 2006-05-14
[QUOTE=stevenash]
Will making a 20 GB NTFS partition be enough for linux?[/QUOTE]

Linux won't live on an NTFS partition.  The Linux file system is called ext3.  GRUB will format correctly if you let it.

---

### Post by skippy81 on 2006-05-14
Use partition magic to delete partitons and make a load of free space, then when you install linux you can just tell it to install into the largest block of free space.  That way theres no risk of getting confused as to which partitions you are going to delete when your in the linux install.

---

### Post by stevenash on 2006-05-14
You guys are the best, thanks for the help!

One last question (another dumb one):

I was just looking at Disk Management in Windows and noticed that for some reason I made my new hard drive a Dynamic Disk (thought I had it as Basic).  Will I need to switch this to a Basic Disk before I start the Ubuntu install or will it be fine?

Also, let's say I use 50 GB total for linux...the other 200 I just want for file storage (music, videos, picture, etc) that can be shared between both Windows and Linux.  I read that FAT32 isn't really a recommended system...will everything be fine if I make the entire 200 GB as FAT32, or should I split the 200 up and make part of it shared and part of it just for Windows?

Thanks, and once again you guys are great!

---

### Post by RRS on 2006-05-14
I think you'll find [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") helpfull, I did.

The formation of the swap partition is semi-automatic using the installation cd, it should read the amount of ram you have and size accordingly.
 
Since your target drive is NTFS you'll want to reformat the entire drive at the begining of the partitioning process to make it all "free space" so be sure you choose the correct drive!

Grub is installed towards the end of the process, when it asks to install to the MBR, select yes.

Although problems are rare, back up your data on the windows drive first, just in case.

Edit: I've heard Partition Magic and Linux don't always get along well.
        The only problem with Fat32 is a limit to the file size you can       use, otherwise it works quite well for sharing data between windows and Linux.

---

### Post by stevenash on 2006-05-14
[QUOTE=RRS]I think you'll find [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") helpfull, I did.
[/QUOTE]
That guide looks very helpful...pictures are goooood.  Time to read up some more. 

Can't say thanks enough for the help, guys.

---

### Post by Sef on 2006-05-15
You're welcome.  If you have questions, please post them.

---

