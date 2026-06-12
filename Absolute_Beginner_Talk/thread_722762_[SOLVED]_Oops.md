---
title: "[SOLVED] Oops?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by merulz on 2008-03-12
I accidentally installed my Ubuntu 7.10 on the same partition as my Vista... is there any way possible to uninstall Ubuntu without wiping my drive or messing up my Windows? I really like Ubuntu, but I want it on a separate partition than my regular operating system.

Side note: If I did install Ubuntu on a different partition, and I wanted to delete it, could I just delete the partition that it is on?

Any help is much appreciated!

---

### Post by Rocket2DMn on 2008-03-12
If you installed Ubuntu over your windows partition, windows and everything on it is gone.  Oops.
You can post the output of ```
sudo fdisk -l
``` so we can see if any NTFS partitions are still there.

You can keep your Ubuntu installation by shrinking your linux partition to make room to install windows again.  You will need to boot from the LiveCD and go to System->Administration->Partition Editor, or use the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
You should always backup your data before fiddling with partitions.  After installing windows again, you will have to restore GRUB since windows will overwrite the MBR - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You can always delete Ubuntu later if you want using either of those LiveCDs to delete the partition.  You can then expand your windows partition to use up the newly freed space, or just format the free space as ntfs or fat32 so windows can read it and use it as a separate partition for data.

---

### Post by merulz on 2008-03-12
I didn't overwrite Vista, just installed on the same partition. I'm on my Vista right now, and I can get on Ubuntu too.

---

### Post by gobuntu on 2008-03-12
Merulz,

It's not possible to install both operating systems in the same partition. They  each require their partition.

If Ubuntu REPLACED Vista, then Vista can not be recovered.

Most likely it could be that Ubuntu installed in a separate partiton, and Vista is still there, but not accessible due to some anomality that can be hopefully corrected.

You may have to recall what you did, or examine what you have, in order for things to begin to make productive sense.

Start to write down messages that show when you turn on your computer.

Best wishes.

---

### Post by gobuntu on 2008-03-12
> **merulz said:**
> I didn't overwrite Vista, just installed on the same partition. I'm on my Vista right now, and I can get on Ubuntu too.

Sorry, this message came after having made my suggestion above.

However, now, what is the problem again?

---

### Post by Dr Small on 2008-03-12
> **merulz said:**
> I didn't overwrite Vista, just installed on the same partition. I'm on my Vista right now, and I can get on Ubuntu too.
Since you can access both, you did not install or overwrite the Vista partition.

---

### Post by merulz on 2008-03-12
Yeah, I installed on the same partition... it's not really a partition but the main drive of my computer. I get the option on the GRUB menu to start 3 different Ubuntu's and 2 different Windows Vista's.

I get the following choices (not exactly what it says, but you get the idea)

Ubuntu -> Default OS booted
Ubuntu something weird -> Never tried opening this
Ubuntu Recover Mode -> As stated
Vista/Longhorn -> The Vista recovery mode
Vista/Longhorn -> The actual Vista

edit: I get no messages when starting up my computer other than the GRUB menu

---

### Post by Rocket2DMn on 2008-03-12
Sounds like you setup a dual boot, post
```
sudo fdisk -l
``` and we'll see what's up.  It sounds like you have it working well.  You probably just have Ubuntu installed on the same HARD DRIVE, on a separate partition.

---

### Post by gobuntu on 2008-03-12
> **merulz said:**
> Yeah, I installed on the same partition... it's not really a partition but the main drive of my computer. I get the option on the GRUB menu to start 3 different Ubuntu's and 2 different Windows Vista's.

I get the following choices (not exactly what it says, but you get the idea)

Ubuntu -> Default OS booted
Ubuntu something weird -> Never tried opening this
Ubuntu Recover Mode -> As stated
Vista/Longhorn -> The Vista recovery mode
Vista/Longhorn -> The actual Vista

Hi, again.

Some of those options are applicable only if you want to boot the operating systems in special trouble shooting modes, or if one has specific needs. No need to click those for now, would say.

Even Windows can boot on different options (for example 'Recovery Mode') etc. 

The GRUB booter is only providing those options that are not needed for common use. 

It does not mean that there are DIFFERENT installations.

There's only ONE of each.

Be happy.

---

### Post by merulz on 2008-03-12
> **Rocket2DMn said:**
> Sounds like you setup a dual boot, post
```
sudo fdisk -l
``` and we'll see what's up.  It sounds like you have it working well.  You probably just have Ubuntu installed on the same HARD DRIVE, on a separate partition.


merulz@merulz-desktop:~$ sudo fdisk -l
[sudo] password for merulz:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1282    10297633+   7  HPFS/NTFS
/dev/sda2   *        1283       58252   457606367+   7  HPFS/NTFS
/dev/sda3           58253       60689    19575202+  83  Linux
/dev/sda4           60690       60801      899640    5  Extended
/dev/sda5           60690       60801      899608+  82  Linux swap / Solaris
merulz@merulz-desktop:~$

---

### Post by Rocket2DMn on 2008-03-12
Yeah, what you have is 2 NTFS partitions.  sda1 is probably a backup partition that came presetup on your computer.  sda2 is your windows vista.  sda3 is your root linux/Ubuntu partition.  sda5 is your linux swap partition. (sda4 signifies that sda5 and everything that might come after is a logical partition).

This is a dual boot setup.  The reason you see multiple Ubuntu options is for standard kernel and recovery kernel.  And each kernel version will have those options (if you have multiple kernels you can choose to boot to an old one, usually used in the case that something goes wrong with your most up-to-date one).  You have 1 Vista installed and 1 Ubuntu installed.

---

### Post by merulz on 2008-03-12
So is there anyway to remove Ubuntu and just install it on a different partition?

---

### Post by Rocket2DMn on 2008-03-12
> **merulz said:**
> So is there anyway to remove Ubuntu and just install it on a different partition?
Hehe dude, it IS on a separate partition, that's what we've been trying to tell you.  Hard drives are partitioned into different areas - that's what a partition is (a piece of a hard drive).  If you google about partitions, you will get a zillion hits on what exactly they are.

---

### Post by merulz on 2008-03-12
Okay, but when I installed Ubuntu, I installed it on the largest contiguous space, which was where my Vista was also located. Is it still on a different partition? And how would I uninstall Ubuntu, I'm kind of tired of having it since I mainly use the computer for gaming, and it doesn't work with any of the games I play. Not looking to play them on Ubuntu, but uninstall Ubuntu.

---

### Post by Rocket2DMn on 2008-03-12
To get rid of Ubuntu, you will need to boot from the LiveCD and go to System->Administration->Partition Editor, or use the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
You should always backup your data before fiddling with partitions. 

Using those, you can delete the linux partitions (root and swap).  You can then expand your windows partition to use up the newly freed space, or just format the free space as ntfs or fat32 so windows can read it and use it as a separate partition for data.  BE CAREFUL to delete the correct partition - you should not be deleting any NTFS partitions.

You will then have to fix the mbr, getting rid of GRUB, so that windows can load normally.  Boot from the Vista cd and enter the recovery console, then run
```
fixmbr
```
You should then have your system as it was before you installed Ubuntu.

---

### Post by merulz on 2008-03-12
Okay, I did as you said. I'm now in a Live session with Ubuntu and on my Partition Editor. I have the following partitions:

/dev/sda1 ntfs RECOVERY 9.82 GiB 5.41 GiB 4.41 GiB
/dev/sda2 ntfs 436.41 GiB 112.10 GiB 324.31 GiB boot
unallocated
/dev/sda3 ext3 18.67 GiB 17.26 GiB 1.41 GiB
/dev/sda4 (lock) extended 878.55 MiB --- --- <unable to delete>
    /dev/sda5 (lock) linux-swap 878.52 MiB --- --- <unable to delete>


My question is, which ones do I delete?

---

### Post by owbizi on 2008-03-12
If I'm **not** wrong:

- sda3 >> the Ubuntu partition;
- sda4 >> an extended partition that contains the swap one;
- sda5 >> the swap partition properly said.

To delete sda4 and sda5, you have to unmount them first. To do this, on gparted, simply right click >> unmount. After that, you can catch... *delete* them all!

---

### Post by Rocket2DMn on 2008-03-13
Oh sorry, I forgot to mention that with the LiveCD, you have to unmount the swap (since it makes use of it).  owbizi has it right.  Delete sda3, sda5, and sda4.  You can then expand or "grow" your Vista partition to use that newly unallocated space.

---

### Post by merulz on 2008-03-13
I am unable to unmount sda4 and sda5. The option is grayed out.

edit: Nevermind, I had to swap it first. Thank you everyone for your help!

---

