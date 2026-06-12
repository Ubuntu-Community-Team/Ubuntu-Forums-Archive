---
title: "Uninstalling on a dual boot?"
date: 2009-07-02
forum: Apple Hardware Users
---

### Post by popplers86 on 2009-07-02
Hi all,

I've been pretty happy with my Mac OS/Ubuntu dual boot, but I've apparently screwed my Jaunty up beyond recognition and it will no longer boot properly.  I'd like to just do a clean install rather than the Intrepid-to-Jaunty upgrade that I did, so I'd like to remove Jaunty and then reinstall it.  Does anyone know how to do this on a dual-booted system without destroying the other partitions (I have Mac OS as well as a shared file between the two)?

Thanks to anyone that can help,
Lia

P.S. I'm still somewhat new to ubuntu and probably need things explained in noob fashion.

---

### Post by papenpj on 2009-07-02
you should be able to just use the install CD and reformat the ubuntu partition only..... at least that is what i do on my windows comps. I have no idea about mac.


of course that means you need to be familiar with what partitions are what.

---

### Post by Sef on 2009-07-02
You would need to manually do the partitioning.   To start, using a live cd, Applications > Accessories > Terminal:

the copy and paste this command in it: 

```
sudo fdisk -l
```

Then copy and paste the results here.  

That command shows what is on what partition.  What you will need to do is delete the intrepid partition and reformat it as root with Jaunty.  First let's see how your system is set up.

---

### Post by ronaldprettyman on 2009-07-02
Run the install cd, once you have the live disc up just delete the partition.

Run the live disk
Once your in the live version of ubuntu opne the terminal
type 
```
sudo fdisk -l
```
Your get a list look for
```
/dev/sda1   *           1       52724   423505498+   7  HPFS/NTFS
/dev/sda2           52725       60801    64878502+   5  Extended
/dev/sda5           53759       60801    56572897+  83  Linux
/dev/sda6           52725       53758     8305542   82  Linux swap / Solaris

```
your will probably look more like this
```
/dev/sda1   *           1       52724   423505498+   7  HFS+
/dev/sda2           52725       60801    64878502+   5  Extended
/dev/sda5           53759       60801    56572897+  83  Linux
/dev/sda6           52725       53758     8305542   82  Linux swap / Solaris

```
The one that says 83 Linux, is the partition that linux is install on. You can use gparted to delete both linux paritions and just do an install to the empty space.

---

### Post by popplers86 on 2009-07-02
Hi Sef and Ronald,

Thank you for the help.  Here is what the command gave:
---------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        3926    31326208   af  Unknown
/dev/sda3   *        3942       15430    92274688    c  W95 FAT32 (LBA)
/dev/sda4           15430       15438       64575    e  W95 FAT16 (LBA)
----------------------------------------

Lia

---

### Post by hajk on 2009-07-02
Well folks, let's be a little careful here in our advice... 

The OP has a GUID partition table, but probably uses the older MBR partition table synchronized with GPT. In that case, having an extended partition /dev/sda2 and all other Ubuntu partitions being /dev/sda5, ..6, etc, will not work, since Ubuntu can only be booted from one of the "primary partitions" numbered 1..4. Since Mac OS X already consumes the first 2 (a small EFI partition plus Max OS X itself), you should at least leave room for a Ubuntu boot partition: one of /dev/sda3 or /dev/sda4. An extended partition is in any case a bit of nonsense with GPT, since Linux booted from one of the primary partitions can use any of the higher numbered GUID partitions (*use* that is once booted, not before).

So, yes, the OP should use the gparted programme that's also on the install CD, then let us know what the partition table looks like before making any changes.

---

### Post by ronaldprettyman on 2009-07-02
> **hajk said:**
> Well folks, let's be a little careful here in our advice... 

The OP has a GUID partition table, but probably uses the older MBR partition table synchronized with GPT. In that case, having an extended partition /dev/sda2 and all other Ubuntu partitions being /dev/sda5, ..6, etc, will not work, since Ubuntu can only be booted from one of the "primary partitions" numbered 1..4. Since Mac OS X already consumes the first 2 (a small EFI partition plus Max OS X itself), you should at least leave room for a Ubuntu boot partition: one of /dev/sda3 or /dev/sda4. An extended partition is in any case a bit of nonsense with GPT, since Linux booted from one of the primary partitions can use any of the higher numbered GUID partitions (*use* that is once booted, not before).

So, yes, the OP should use the gparted programme that's also on the install CD, then let us know what the partition table looks like before making any changes.

Good point. Put in the Mac OS installation disc, and do a disc repair, you can remove the Linux partition from their.
[http://kb.wisc.edu/helpdesk/page.php?id=3810](http://kb.wisc.edu/helpdesk/page.php?id=3810)
Gparted usually causes error with EFI, if you ever try to use bootcamp it will come up and tell you, you need to repair any way. You should be able to fix it from the Disc Utility in osx.

---

### Post by popplers86 on 2009-07-02
Hi all,

I ran the install from the live disc to get to the partitions, and this is what I found (from left to right):

Mac OS X (/dev/sda2): 29.9 GB
Free space of 3 KB
DATA (My shared documents partition) (/dev/sda3): 88 GB
Occupied space of /dev/sda4: 63.1 MB (bootcamp?)
Ubuntu 9.04 (/dev/sda5): 29.5 GB

Thanks again,
Lia

---

### Post by popplers86 on 2009-07-04
Hi there,

I'm trying to be cautious given hajk's warning.  Now that I've posted what my partitions look like, do Ron's instructions to remove my Ubuntu partition through Mac's install disc stand?

Thanks,
Lia

---

