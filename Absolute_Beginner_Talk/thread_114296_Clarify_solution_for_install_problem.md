---
title: "Clarify solution for install problem"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by enricodc on 2006-01-08
Hi,
This is my first post and it will no doubt show up how little I know about Linux. I'm having the same installation problem as some other people reported "install hangs at partitioner". A reply in the other forum stated:

"I had the same problem. I deleted all partitions the primary harddisk and restarted the machine. The problem went away. I guess there is a problem with the installer if there are no more space in the primary hd."

Could someone explain to me how to do this? 

I want to run a 500MHz 64MB system purely as a Linux server, no Windows partition necessary. It is an IBM Aptiva that was running Win98SE. I have formatted the hard disk (only one) using the format command with a Win98 boot floppy but the Ubuntu 5.10 install continues to hang at 52% of partitioner.

Do I have to partition the disk in a specific way before installing Ubuntu?
Thanks.
Cheers.

---

### Post by paddyg on 2006-01-08
Have you used the ext3 filesystem? Linux shouldn't use windows fs.

---

### Post by estel on 2006-01-08
Might involve formatting the HD on the installer, or something.

Are you using the server install? :)

---

### Post by enricodc on 2006-01-08
[QUOTE=paddyg]Have you used the ext3 filesystem? Linux shouldn't use windows fs.[/QUOTE]

No, I don't know how to do that. This is my first attempt to install a linux system. Do you know where there are instructions for setting up the disk partition prior to an install? Can I do it with the install CD I already have?

:)

---

### Post by enricodc on 2006-01-08
[QUOTE=estel]Might involve formatting the HD on the installer, or something.

Are you using the server install? :)[/QUOTE]

:) 

Yes. Using server install but don't know how to partition or format the HD for Linux prior to running the server install. Any pointers?

---

### Post by az on 2006-01-08
[QUOTE=enricodc]Hi,
I want to run a 500MHz 64MB system purely as a Linux server, no Windows partition necessary. It is an IBM Aptiva that was running Win98SE. I have formatted the hard disk (only one) using the format command with a Win98 boot floppy but the Ubuntu 5.10 install continues to hang at 52% of partitioner.

Do I have to partition the disk in a specific way before installing Ubuntu?
Thanks.
Cheers.[/QUOTE]

The installer needs 128 megs of ram to work.

Actually, you can get by with less, but 128 is recommended.

---

### Post by Brigrat on 2006-01-08
I am pretty sure that the installer will take care of your partition issue as well as format when you atart the loader.  I am using an old with 400mhz and a scsi HDD.  The system took right off as question about the loader software.  If the box will see the cd on boot up you should be alright.

---

### Post by Terry of Astoria on 2006-01-08
I have run into that kind of behaviour before. I found that if I REMOVED all partitions from the drive it helped. You might try booting up yer windows boot flop and type 
fdisk
at the prompt. answer "y" to treat partitions as large or whatever, then use the menu to remove any partitions and any logical drives.
  It might help make the partitioner stop freezing. 
'course you might just not have enough RAM! Geez. Another 64 would help. Someone must have one for you. Ask around. Should be cheap or free.
You can test RAM by booting the live CD and then at the prompt type
memtest then hit enter.

---

### Post by blair on 2006-01-08
You should be able to use (or create if necessary) a Windows boot disk and then fdkisk your hard drive from there, blowing away all the partitions. This will ensure you have a clean hard drive when you start the Ubuntu install process. If the problem still persists, it may well be your 64Mb of memory is simply insufficient. 

Alternatively, you could try a differerent Linux distro altogether that is optimized for old, resource constrained PCs. DSL for example is a one of the lightest Linux distros out there. The site is: 

[www.damnsmalllinux.org](www.damnsmalllinux.org)

---

### Post by enricodc on 2006-01-08
Success! Thanks everyone for your help. General opinion was that the stall at 'Partitioner' was either due to not enough RAM (64MB in this one) or that I needed to remove all HD partitions before commencing install. 

I used fdisk on the Win98 boot floppy to delete the one and only primary HD partition, then the install got past the dreaded 52% of the Partitioner progress bar.

It is still unpacking the base system. I will get another 64MB RAM anyway. That seems very good advice.

Cheers
:D

---

