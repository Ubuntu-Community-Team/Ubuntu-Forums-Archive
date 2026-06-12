---
title: "clean Dual Boot help needed"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by futureal2032 on 2007-08-13
Hi all,
i am a linux beginner... (i can install/upgrade/use but don't know much about trouble shooting or R&D)

I have previously installed dual boot systems using various windows and linux (i.e. xp & ubuntu 5.10, 98 &  redhat, vista & fedora etc.)

i have no knowledge about installing two linux distros on the same system.

[COLOR="Red"][SIZE="4"][B]Environment: 
I have a P4 D3.0GHz with 2GB 667MHz DDR2 and Seagate SATA 250GB hard disk.

The Hard Disk is empty. I want to install Fedora (Core 5 or 7) and Ubuntu 7.04.

Question: 
1. How many Partitions should i make?
2. What will be the ideal/good partition scenario. (any model partition table)?
3. What distro should i install first?
4. What grub should i install on mbr?
5. Are there any issues regarding size of hard disk or RAM?[/B][/SIZE][/COLOR]

[SIZE="2"][B]also i am using Ubuntu 5.10 on my system using 256MB RAM (32MB shared with on-board display)
i got a Ubuntu 7.04 CD ...can i upgrade my 5.10 with this CD. Will 7.04 install on 256MB RAM?[/B][/SIZE]

---

### Post by Arthur Archnix on 2007-08-13
I read somewhere that if you ask two different  people how to partition a hard-drive for a dual-boot scenario you'll get three different answers. But let's get the obvious out of the way:

Put a swap at the end of about 1GB. Create two Ext3  partitions at the start that are 4.69 GB. These will hold everything to do with each OS. Why 4.69? So you can burn your OS  to a DVD using Partimage and have an easy way to restore it. If this doesn't interest you then make each about 10GB. Make the rest into one big partition for all your files, music, movies, etc.

A lot of people say to put /home on its own partition, so that if you ever need to reinstall your settings are still there. But me, if I'm reinstalling something it's because i want a clean setup, so that's never appealed to me. I put / and /home on the one 4.69GB partition.

---

### Post by futureal2032 on 2007-08-13
> **Arthur Archnix said:**
> I read somewhere that if you ask two different  people how to partition a hard-drive for a dual-boot scenario you'll get three different answers. But let's get the obvious out of the way:

Put a swap at the end of about 1GB. Create two Ext3  partitions at the start that are 4.69 GB. These will hold everything to do with each OS. Why 4.69? So you can burn your OS  to a DVD using Partimage and have an easy way to restore it. If this doesn't interest you then make each about 10GB. Make the rest into one big partition for all your files, music, movies, etc.

A lot of people say to put /home on its own partition, so that if you ever need to reinstall your settings are still there. But me, if I'm reinstalling something it's because i want a clean setup, so that's never appealed to me. I put / and /home on the one 4.69GB partition.

so as u say it will be like 
/ 4.69gb (or 10gb)
/ 4.69gb (or 10gb)
/usr rest of the space
swap 1gb 

is that correct??

---

### Post by Arthur Archnix on 2007-08-13
Sorry no.

4.69  ext3   Ubuntu
4.69  ext3   Fedora
###   ext3   Files
1.00  Swap

When Ubuntu installer asks what to do with the Fedora partition, I tell it to put it in /mnt/fedora.
When Fedora asks tell it to put Ubuntu in /mnt/ubuntu

I put the Files partition in /mnt/files, but it could also go in /media if you want ubuntu doing what it wants with it. I like to control where it shows up though so I put it in /mnt

Definitely do not mount it at /usr

---

### Post by paradoc on 2007-08-13
Someone (I forget who!) posted these screencasts the other day........you may find all you want here and a little bit more, it's ideal starter stuff for anyone wanting to dual-boot, but don't forget (those with a busy XP drive--not you, furureal) to defrag and scandisk first in Windows before adding another OS.[http://rlugubuntuhelp.blogspot.com](http://rlugubuntuhelp.blogspot.com)

---

