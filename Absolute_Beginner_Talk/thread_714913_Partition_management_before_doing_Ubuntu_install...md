---
title: "Partition management before doing Ubuntu install..."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by HitRefresh on 2008-03-04
So far I've boot with a Gutsy live CD on a HP laptop and it seemed to go well (yay!) 
 I am going to do a full install of Gutsy or maybe Fawn.

 But before I do, I needed some guidance on partitioning. 

After doing the "Shrink Volume" in Vista my 160GB looks like this:
-C drive (with Vista) = 96GB
- Unallocated Space = 40GB
- HP Recovery = 11GB

I'd like to do a dual boot, which I've found instructions for already. But I'd like to have Vista in one partition and Ubuntu on another. Also I'd like to be able to read/write/transfer files between them w/o re-booting. I don't know what my next steps are to do this. 

Do I need to do anything further in Vista to the unallocated space ? And then what would I select in the Ubuntu install step for "Prepare Disk Space" ?

Thanks for any help.

---

### Post by Baelari on 2008-03-04
don't need to do anything to the unallocated space with vista
do manual for preparing disk space, automatic will wipe vista, i think

---

### Post by forestpixie on 2008-03-04
you don't need to do anything else in vista

when you get to the partition part of the install - you'll get a few choices, one will use free space I believe

However I tend to do the partitioning before I boot the livecd, but you could use manual method

create an extended partition using the unallocated space and then make logical partitions within that to install to

you can have /home seperate - bit like docs and settings in windows, but when you come to reinstall, upgrade you can keep the same /home folder

to do that - 

create a root partition - mount point needs to be / - I found 8Gb more than enough for me

create a swap partition, size dependent on your ram - not necessarily needed if you have loads of ram unless you want to hibernate or use memory intensive apps 

create a /home partition - mount as /home - this will be whatever you have left

If you don't want to do that you can use the option that says something along the lines of 'use free space'

Make sure you've got backups - you're mucking about with partitions whichever way you do it 

have a look here 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Good luck

whatever you do - the USE WHOLE DISC will do exactly what it says on the tin and you will lose vista

---

