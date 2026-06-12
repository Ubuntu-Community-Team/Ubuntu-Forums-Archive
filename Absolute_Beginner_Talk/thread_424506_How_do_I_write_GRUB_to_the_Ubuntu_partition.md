---
title: "How do I write GRUB to the Ubuntu partition?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-26
Topic combined with my old topic.

[http://ubuntuforums.org/showthread.php?t=424040](http://ubuntuforums.org/showthread.php?t=424040)

---

### Post by louieb on 2007-04-26
hd0 is the MBR of the first hard drive.
>  It's installing Ubuntu to Partition #4 os SCSI1 (0,0,0) (sda) as ext3GRUB numbers partitions starting with zero. So in GRUB speak the 4th partition of the first drive wound be (hd0,3).  Or in a Linux /etc/fsab file it would be called /dev/sda4.   

Having said that I don't have a clue which partition Partition #4 os SCSI1 (0,0,0) (sda) refers to. 
I guess you used manual partitioning. IF you made /dev/sda4 the mount point for / (root) the to install GRUB to that boot sector use (hd0,3).
See the Dual Boot link in my signature for more information.

---

### Post by gohanssjn on 2007-04-26
Awesome, thanks.  Trying (hd0,3) now to see what happens!

---

### Post by gohanssjn on 2007-04-26
Sadness, put (hd0,3) and it still wrote to the MBR.  Time to restore from a Ghost and try something else.

Ideas?

---

### Post by louieb on 2007-04-26
That weird. I install grub to partitions fairly often. What were you using to install GRUB?

---

### Post by gohanssjn on 2007-04-26
I was letting Ubuntu FF do it, but switching what I said at the end of the install.  Installing off the LiveCD I believe.

---

### Post by louieb on 2007-04-26
Haven't installed Feisty from the live. Did from the alternate CD. GRUB installed to the Feisty partition no problem.

---

### Post by gohanssjn on 2007-04-26
The LiveCD is the one that boot's into Ubuntu, then installs, right?

Total noob here, lol.

By the way, thanks for all the info so far :D

---

### Post by louieb on 2007-04-26
> **gohanssjn said:**
> The LiveCD is the one that boot's into Ubuntu, then installs, right?:D
Right. No problem. 
Glad you backed up before you started. 
What are you using for your boot manager?
If you have internet with the live CD will you list your partition table?
to do that open Applications>Accessories>Terminal and enter
```
 sudo fdisk -l
``` (as in little). 
Should be able to get GRUB where you want it. Check the Psycho cats link theres a good explanation of live CD install.

---

### Post by gohanssjn on 2007-04-26
Well, it's going to be a bit it seems >.>

I restored my Ghost, but then NOTHING would boot, so I am doing it partition by partition now.

---

### Post by gohanssjn on 2007-04-26
I am entering sudo fdisk -l and getting nothing back.

Says it can't open /dev/sda

---

### Post by gohanssjn on 2007-04-26
OMG, got it to read.

Ok, here is what I have

................Boot.....ID .........System
/dev/sda1......*.........7...........HPFS/NTFS
/dev/sda2................7...........HPFS/NTFS
/dev/sda3................f...........W95 Ext'd (LBA)
/dev/sda5................dd.........Unknown

Wehn I install, it says it's creating 4 and 6, so I guess I need to find a way to install Grub to 4?

---

### Post by gohanssjn on 2007-04-26
Ok, if I manually partition, it makes partition 6 and 7, but I only have 1,2,3,5.  No 4.

---

### Post by gohanssjn on 2007-04-26
WOW, ok, Grub still exists on my MBR...BUT...I can boot MediaDirect!  Interesting.  This will do for now!

---

### Post by louieb on 2007-04-27
Look like sda1, sda2,sda3, are primary partitions. Since sda4 is not listed it is has to be an extended partition, but should still show up in the fdisk output.
sda5 is a logical partition. You can alway tell if a partition is logical it will have a partition # of 5 or greater.
[B]You do not want to install GRUB to sda4 
[/B]more that likely you want to put it in **sda5.**
But I still would like to see the real fdisk output after you install. 
BY way of example here the fdisk out of a computer that Boots XP, Ubuntu Dapper and Feisty and PCLinuxOS. 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10207    81987696    7  HPFS/NTFS
/dev/sda2           10236       11528    10386022+  83  Linux
/dev/sda3           24257       24321      522112+  82  Linux swap / Solaris
/dev/sda4           11529       24256   102237660    5  Extended
/dev/sda5           11529       12821    10385991   83  Linux
/dev/sda6           12891       16663    30306591   83  Linux
/dev/sda7           16664       17999    10731388+  83  Linux
/dev/sda8           18000       23167    41511928+  83  Linux
/dev/sda9           23168       24256     8747361    b  W95 FAT32


```You have something strange with the  extended partition not showing up. 
May want to do a little Googeling and get a rough idea of what primary, extended and logical partition are all about.  [Heres my page on Partitions]("http://louboldt.com/ilinuxpart.htm") it contains a few links to help you learn more.    Knowing something about Partitions sure helps when trying to Duel Boot.

---

### Post by gohanssjn on 2007-04-27
Ok,  am out of town for the weekend, and I may have screwed something up last night trying to enable the Nvidia card I have (I got half way through the FF Nvidia fix, the long way, and couldn't edit what I needed to, but then just did the two command fix see listed everywhere), so I'll get an fdisk readout for you on Sunday!

EDIT: Topic on NVidia checking:[http://ubuntuforums.org/showthread.php?t=425016](http://ubuntuforums.org/showthread.php?t=425016)

---

