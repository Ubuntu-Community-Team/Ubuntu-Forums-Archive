---
title: "my ubuntu wont install - free me from windows!"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by drowner on 2006-01-13
Hey guys

went to install ubuntu, went along pretty cruisy... until the DHCP thing didnt work... dont know why. quit and started again, same thing. so i said not to worry.

it carried on. Partition time

I went for the manual partition, and nothing happened. Zilch. (I went for the non-deleting option)

then i tried guided partition... and it said there was no free space. THing is, i know how much space there is on the HD. Although its all NTFS formatted, there is space.

SO whats going on? Help!!!!

---

### Post by Sef on 2006-01-13
> Although its all NTFS formatted

Linux can not write to NTFS.  You need to format the hard disk to FAT32 for the Ubuntu install.  If you have a home or root or both directories, they can be formatted to ext3 or reiserf.  Swap is formatted to swap.  The windows partition can remain formatted as NTFS.

---

### Post by drowner on 2006-01-13
[QUOTE=Sef]Linux can not write to NTFS.  You need to format it to FAT32 for the Ubuntu install.  If you have a home or root or both directories, they can be formatted to ext3 or reiserf.  Swap is formatted to swap.  The windows partition can remain formatted as NTFS.[/QUOTE]

cool thanks.

but how do i get another partition on there... i was under the impression the install program would partition the HD and reformat for me

---

### Post by Sef on 2006-01-13
The partioner is on the install disk. Read this tutorial to find out how to dual boot:

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

I used it when I first dual booted Ubuntu with Windows XP.

---

### Post by drowner on 2006-01-13
[QUOTE=Sef]The partioner is on the install disk. Read this tutorial to find out how to dual boot:

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

I used it when I first dual booted Ubuntu with Windows XP.[/QUOTE]


i was following that guide.... but when i got to the partition stage, i went manual partition, picked the hda in question (theres only one) and went to change the size... and nothing happened

when i went for the guided partition option... it said there was no space

---

### Post by kosmic on 2006-01-13
IF you use the Partition program on the disk install, and your drive is NTFS you need to ERASE the partition first, and the you can create the / and /home partitions :)
 
 
ATTENTION : IF YOU DO THIS WINDOWS IS GONE FOR LIVE

---

### Post by Michael Steinberg on 2006-01-13
Don't give up hope--you can use QTParted from a Knoppix disk, or the Windows PartitionMagic program, to shrink NTFS partitions. Ubuntu's installer won't do the trick, though some of the documentation says it will. I had the same problem setting up my laptop to dual-boot.

---

### Post by drowner on 2006-01-13
[QUOTE=kosmic]IF you use the Partition program on the disk install, and your drive is NTFS you need to ERASE the partition first, and the you can create the / and /home partitions :)
 
 
ATTENTION : IF YOU DO THIS WINDOWS IS GONE FOR LIVE[/QUOTE]

not that im fond of windows, but if its all the same id rather keep it :D 

 i read that guide, and it seemed to say that it wouldnt damage my windows partition.... even if it was NTFS

---

### Post by drowner on 2006-01-13
[QUOTE=Michael Steinberg]Don't give up hope--you can use QTParted from a Knoppix disk, or the Windows PartitionMagic program, to shrink NTFS partitions. Ubuntu's installer won't do the trick, though some of the documentation says it will. I had the same problem setting up my laptop to dual-boot.[/QUOTE]

ahh. so the installers partition program WONT shrink an ntfs partition. 

that makes sense i spose.... although i read differently

lol... i basically tried everything, a variety of different numbers... i was like at a 'JUST PARTITION SOMETHING' stage :D

then i rebooted and windows fully messed itself. :D its  ok now though.

---

### Post by Sef on 2006-01-13
>  the Windows PartitionMagic program

P M has been known to not like Linux/GNU too much, so it is best to avoid it.

> I wrote up this on setting up XP and Linux as a dual boot:

Quote:
1) Install Windows first

2) When it gets to partitioning, use 'manually partition' (similar words-it's the bottom option.) Below is from a previous post of mine:


Quote:
Re: Partitioning Problems - 5 Days Ago 
I) If there is no free space on the disk, do this:

A) Highlight the partition you want to shrink. 

B) Highlight the disk size. 

C) Erase the numbers on the screen and write in the new size of the partition - XX.X GB . 

- Don't forget to put GB

4) Click on the button. (I think it says 'OK'.)

5) Then click on 'Done Partitioning This Disk' (or something similiar, it's the top option.)

II) Two Partitions Now

A) One which says NTFS and one that says Free Space.

1) NTFS is the XP partition
2) Free Space can used to set up Ubuntu Linux.

-) It's a good idea to maually partition, and set up a /home directory, so when you upgrade Ubuntu, your files and settings won't be overwritten.

---

### Post by drowner on 2006-01-13
Cheers sef.... i reckon i done all that....


like changed it to 10.0 GB... i even think i left it in capital letters/// :confused: 


it does nothing!.. maybe i gotta get PM and hack off a few gigs before installing the ubuntu. sounds like the only way

---

### Post by Michael Steinberg on 2006-01-13
I had the same problem--I'd change the size and nothing was actually changed. Did this a number of times before I changed my approach.

If you can download Knoppix or another live CD with QTParted, or any live CD with a recent version of cfdisk I'd suggest you try that. I haven't found problems with PM myself, but since at least one poster suggests that it may cause problems you're probably safer using Linux tools for your partitioning

---

### Post by drowner on 2006-01-13
[QUOTE=Michael Steinberg]I had the same problem--I'd change the size and nothing was actually changed. Did this a number of times before I changed my approach.

If you can download Knoppix or another live CD with QTParted, or any live CD with a recent version of cfdisk I'd suggest you try that. I haven't found problems with PM myself, but since at least one poster suggests that it may cause problems you're probably safer using Linux tools for your partitioning[/QUOTE]

but if i hack off half my hd before i even start to install it with PM.... then i can reformat that as fat, it should be fine... it doesnt need to know that linux is going to live there!

---

### Post by Michael Steinberg on 2006-01-13
Yes, that would make sense--reduce your NTFS partition, partition the remainder as something else that Ubuntu will then reformat. There's just the voodoo aspect of computing--you know, there's some little flag or something that a progam will set without telling you that screws up something else miles down the road. as i said, i'd probably have done as you suggest, only I didn't have a bootable PM setup handy--I was working on a machine without a floppy, and my PM was in two floppies. It was easier to grab a Linux Live CD. But I'd guess the odds are good that you can get the job done safely with PM.

Good luck!

---

### Post by drowner on 2006-04-15
Just thought id update!

I eventually got it done... any noobs out there... my key was to run windows consecutively doing Defragments... both in XP AND in DOS.

Over and over and over and over and over and over again ;)

THEN Ubuntu partitioned it at the next install ;)

---

