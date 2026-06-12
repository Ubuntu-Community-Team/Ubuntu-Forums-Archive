---
title: "Mounting Extended Partition"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by SimonHalliday on 2008-02-25
I have been looking at several of the other posts and trying to work out what I am doing wrong. I am very new to Ubuntu. 

I ran the following command in the terminal to have a look: 

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ffc9ffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       31280    97659135   83  Linux
/dev/sda4           59851       60801     7638907+   5  Extended
/dev/sda5           59851       60801     7638876   82  Linux swap / Solaris



I added the following line to the /etc/fstab:
/dev/sda4 /media/fat32 vfat   defaults,utf8,umask=007,gid=46 0 1

I created the folder for the mount point
sudo mkdir /media/fat32

I then tried to mount it by typing:
sudo mount -a 

And got the following comments. 

 wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can anyone tell me what I'm doing wrong?

Thanks for your time.

---

### Post by SimonHalliday on 2008-02-25
I should also comment that I am using a dual boot - my wife and I are weaning ourselves off of windows.

---

### Post by housam on 2008-02-25
Read [[COLOR="Red"]_this thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=608348&highlight=mounting+ext3+partitions")it may help

---

### Post by SimonHalliday on 2008-02-25
I tried looking at that and using Pysdm, however my sda4 doesn't come up in the list of drives (yes, I've tried to refresh it). My sda 1, 2 and 5 come up but not 4.

---

### Post by housam on 2008-02-25
> **SimonHalliday said:**
> I tried looking at that and using Pysdm, however my sda4 doesn't come up in the list of drives (yes, I've tried to refresh it). My sda 1, 2 and 5 come up but not 4.

 sda4 is the extended partition . it'll not show up.( it contain the swap partition)

---

### Post by SimonHalliday on 2008-02-25
What does that mean though? I have 250GB of space in a fat32 partition that I can't access.  If the 'swap' is nominally in sda5, what then is in sda4, which you say contains the swap.  How do I gain access to the rest of it?

---

### Post by housam on 2008-02-25
> **SimonHalliday said:**
> What does that mean though? I have 250GB of space in a fat32 partition that I can't access.  If the 'swap' is nominally in sda5, what then is in sda4, which you say contains the swap.  How do I gain access to the rest of it?

That means that you have some unallocated space ( not used ) inside the extended partition beside the swap partition.
 All what you've to do is to use Gparted tool ( on the live cd ) to create more partitions inside that extended one.

---

### Post by mozetti on 2008-02-25
According to your partition table, you **don't** have a 250GB fat32 partition.

sda4 is you extended partition. Think of it as a "dummy" partion - you can't use it as a read/write partition, it's just a container for any logical partitions you put in there. It's the logical partitions that you can mount and use.

Let's look at your partition table:```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 19122 153597433+ 7 HPFS/NTFS
/dev/sda2 19123 _31280_ 97659135 83 Linux
/dev/sda4 _*59851_ 60801 7638907*+ 5 Extended
/dev/sda5 *59851 60801 7638876* 82 Linux swap / Solaris
```

Note the parts that I underlined - Partition #2 ends on block 31280, but partition 4 doesn't start until block 59851. There is some unallocated space there, but there is no partition on it.

Note the parts that I italicized - Your extended partition runs from blocks 59851 to 60801. Your swap partition also runs from 59851 to 60801. This means that the swap partition is using up all the available space in the extended partition. That's fine, by the way. Don't listen to the post above me -- you don't have any unallocated space in your extended partition, per my discussion above.

The only unallocated space you have on your disk is between Partition 2 and Partition 4 -- you can make a primary partition there, Partition 3 and use that space. There can only be 4 primary partitions on a disk, that's why we use extended partitions. An extended partition is a primary partition that serves as a container for logical partitions, so that you can have more than 4 total partitions on a disk. For example:```
Part 1 - primary partition - 100GB
Part 2 - primary partition - 50 GB
Part 3 - primary partition - 50 GB
Part 4 - extended parttition - 300 GB
---Part 5 - logical partition - 100 GB
---Part 6 - logical partition - 100 GB
---Part 7 - logical partition - 50 GB
---Part 8 - logical partition - 50 GB
```


My advice would be to install/use gParted to get a visual view of your disk. It may make things easier.

---

### Post by housam on 2008-02-25
> **mozetti said:**
> 

The only unallocated space you have on your disk is between Partition 2 and Partition 4 


.

Yes , you are right . I just miss locate the unallocated space.

---

### Post by SimonHalliday on 2008-02-25
Thanks so much.  I will install the program and try that. Will get back to say if it works.  I'm still getting used to having to control everything, never mind being able to be in control of everything, in Linux.

---

### Post by SimonHalliday on 2008-02-25
Problem solved. Thanks.  I used gParted followed by PySDM.  All worked very well.  Still need to learn how to edit the /etc/fstab properly but that will come with time.

---

