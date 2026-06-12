---
title: "New try, new AAAARGH!"
date: 2010-06-20
forum: Apple Hardware Users
---

### Post by c-a-b on 2010-06-20
My Hardware: 
iMac G5 20", 2.0 GHz PPC G5 single processor, 2 GB DDR SDRAM, ATI Radeon  9600 AGP with 128 MB VRAM, 250 GB Maxtor Harddisk, PIONEER DVD-RW  Superdrive.

After my unsatisfying trials in getting network again in Ubuntu 10.04 PPC, I decided to give it a fresh start with a new installation. But that isn't easy, too! ](*,)

Restaurating the 30 GB hard disk that I used for Ubuntu before didn't work at all because it puzzeled it into many pieces of some MB to some GB and cleaning that mess up is horrible! Whatever I try to add some spaces, there is one rest left after another mini-partition that cannot be deleted or whatever, befor that is another mini-partition and so on. I managed that almost 29 GB were taken at once, but with that partition I cannot work anymore because Ubuntu Live CD isn't accepting this space as installation free space! But it says that there is a 900 MB space left to install whats too tiny to install at all. YEEHA! ](*,)

So, there are 29 GB free again but Ubuntu isn't willig or able to use it, there are much idiotic mini-partitions and I get stupid on that all! 

Suggestions? Please?

---

### Post by quixote on 2010-06-22
You should be able to use gparted to combine partitions you're not using. Boot with a livecd of, for instance Lucid, 10.04.  Let's say, for instance, you have the following partitions:

/dev/sda1     *  ntfs (=boot partition) 5GB  Windows
/dev/sda2        3GB  something useless
/dev/sda3         2GB ext3 Linux data partition that you want to keep
/dev/sda4        100MB partition from god-knows-what
/dev/sda5        2GB partition
/dev/sda6        1GB ext3 another Linux data partition 
/dev/sda7        1GB  vfat data partition 
/dev/sda8        2GB something useless.

Let's say you'd like move all the data partitions to one end of the drive, and put all the remaining space together in one partition that's big enough for Ubuntu. (Apply and wait for each operation as you do it.  Gparted can get confused if too much is stacked up for it to do.)

1) Delete sda8.  That turns it into "free space".
2) Move (or copy?) sda3 into what was the sda8 space
3) delete sda2, what was sda3 if there's still duplicate data there, sda4, and sda5.
4) format all that contiguous free space into one 7GB ext4 filesystem where you will later install Lucid.

For your specific situation, map out on paper all the little partitions, and figure out what to move where most efficiently before you start.  As you say, dealing with all that is very tedious, but there's no way around it.

As for why it's not letting you delete some partitions, I'm not sure.  Can you post the error message?  Remember that you can't do any operations on a mounted partition.  If it's mounted, it'll have a lock symbol next to it.  That's why you need to boot from a livecd.  If the partitions have been mounted automatically, select it in gparted, got to "Partition" and then select "unmount".  After that it should let you deal with it.

When you have more questions, just ask :D

---

