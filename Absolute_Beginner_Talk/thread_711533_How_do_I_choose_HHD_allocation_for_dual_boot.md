---
title: "How do I choose HHD allocation for dual boot"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by regbsn on 2008-02-29
I have my XP and windows programs down to 7.6 G with 10.7 free space and XP swap at 512MB to conserve space. Of the 7.6g I have 1.5 to 2 G of Windows programs. Can I place the programs on the shared data partition so that Wine could use them on Linux. I assume that the XP swap has to stay on the XP partition.


Possibilities:
XP / XP swap partition (only if swap can't be on shared data partition)
NTFS shared data partition with Windows programs also
"/" partition
"/ home" partition
"Linux Swap partition

XP/XP swap partition/Windows programs
NTFS shared data
"/" partition
"/ home" partition
"Linux Swap partition

Why not (just curious)
XP/XP swap partition/Windows programs/shared data
"/" partition
"/ home" partition
"Linux Swap partition

I am reformatting my drive for a clean install of XP Home (My Product ID key on XP Pro OEM has been recently classified my Microsoft as compromised aka possible copy. I Re-installed it twice in 2 weeks).
I am hoping for suggestions for partition size and above listed schemes.
I have the format on hold awaiting suggestions. Also, should I format the non NTFS partitions? That is should I create one or two NTFS partitions and a third unformatted space for Ubuntu or two NTFS partitions with the second one large enough to repartition with Gparted during Ubuntu install.
 Thanks,
Anxiously waiting,
Reese

---

### Post by Crooksey on 2008-03-01
If your programs are on your XP partition, then you can still run them with wine.

---

### Post by regbsn on 2008-03-02
So far I have deleted my single NTFS Partition leaving me with 19077Gig. I created a 7Gig NTFS (6.83Gig usable) partition for and installed XP Home instead of XP Pro to save space. the rest unpartitioned.

So on o the other partitions.

Should I put the NTFS data partition next then the Ubuntu partitions?
Can I put Windows programs on both the XP partition and the Data partition? This would allow me to allow more space for XP swap file and Restore files.

How big should the "/", the "/ home and the swap file be?
What order should they be in? I know that a mounted partition can't be resized, so I was wondering the needed order to allow needed resizing in the future?

Thanks,
Slow learner,
Reese

---

### Post by cbs2186 on 2008-03-02
> **Crooksey said:**
> If your programs are on your XP partition, then you can still run them with wine.

How?  I posted asking if this was possible and was met with a fairly unanimous "no".  In fact, I was told that the programs would need to be installed in Wine's fake-windows file system to be usable with wine. 

Not doubting you, as I have no experience (haven't even finished my Linux OS install yet), but if you could give instructions for how that would be wonderful.


Edit:  So I don't cause thread drift, the original post I am referring to is here: [http://ubuntuforums.org/showthread.php?p=4439612&posted=1#post4439612](http://ubuntuforums.org/showthread.php?p=4439612&posted=1#post4439612)

---

### Post by regbsn on 2008-03-04
Please somebody tell me if I finally am getting an understanding!

Primary and logical partitions:
Primary 1.......................= (NTFS) XP <XP and Windows Programs>
Primary 2.......................= (NTFS) Data 
Primary 3.......................= (ext3)
Extended from 3
_Logical 1......................= (ext3) "/ home" <settings/preferenves>
_Logical 2......................= (ext3) "/"  <Ubuntu and programs> 
_Logical 3......................= (swap) Linux swap

Does this work? I was thinking that this would keep data safe in  P2. And allow me to reinstall Ubuntu upgrades as they become available.

I was just wondering as I was looking at this. Is Primary 3 viewed as a different partition from the extended partition. If it is, should I put "/ home" or "/" on it?

This way if I ever decide to make a Grub partition (I assume it needs to be a primary) and figure out how to do so, I have one primary partition allocation left. How to do that I would imagine would be yet another post.

I am sorry if I asked to much in one post.
Thanks,
Reese

---

### Post by logos34 on 2008-03-04
> **regbsn said:**
> 
I was just wondering as I was looking at this. Is Primary 3 viewed as a different partition from the extended partition. If it is, should I put "/ home" or "/" on it?

This way if I ever decide to make a Grub partition (I assume it needs to be a primary) and figure out how to do so, I have one primary partition allocation left.

The layout you have is fine. 

Primary partition 3 **is** the extended--think of it as a container or shell that holds logical partitions.  (stricktly speaking, an extended is just a special type of primary partition that can be subdivided up). /home, / and /swap will be numbered as 5-7 depending on the order they were created in.

A [separate grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") can be either primary or logical, doesn't matter (although you might not want to waste you last primary on a tiny grub partition.)  Put it anywhere you want.

---

### Post by regbsn on 2008-03-29
Okay, letme see if I have this right.
In my example, partition 1 is primary, partition 2 is primary, partition 3 as an extended partition is a primary partition that is subdivided into logical partitions? Therefore I am only using 3 primary partitions.

If this is the case:
_Primary 1 is XP (NTFS)
_Primary 2 is shared data (NTFS)
_Extended Logical (Takes place of Primary 3)
__Logical 1 "/ home" (ext3)
__Logical 2 "/" (ext3)
__Logical 3 Grub (1Mb)(ext3) at very end of hard drive

Should LINUX SWAP be L3 or L4?

This way I can change size of P2 and L1 as needed... or can I?

I wanted the shared data to be NTFS so that as I added and removed data  I could defrag. I read that ext3 could not be defragged. I also read where somebody thought that ext3 defragged automatically every 30 boots.

Can I shrink P2 and expand L1 without destroying data? Would I rally need to? If so, why?

Where does the DE reside?

Last question for this post:
How big should each be if I want to try different DE's?

Thanks,
Reese

---

