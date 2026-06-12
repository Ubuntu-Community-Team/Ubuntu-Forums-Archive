---
title: "Complex Partition Issues"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by antihero on 2007-02-08
Hey everyone!

My Dell e1405 laptop, which I bought 2 months ago, came partitioned like this:

Partition 1 - Diagnostics partition (vfat)
Partition 2 - XP partition (ntfs)
Partition 3 - Dell Media Direct partition (vfat)
Partition 4 - Restore partition (vfat)

I left the default partitions in tact but shrunk the XP partition and installed Ubuntu. Both operating systems have been working flawlessly for 2 months.

The other day, when I booted up, it said something about Media Direct (maybe I hit the MD button?) and then gave me a blue screen of death:

> A problem has been detected and Windows has been shut down to prevent damage to your computer. Plug and Play detected an error most likely caused by a faulty driver. If this is the first time you've seen this Stop error screen, follow these steps:

Check to make sure any new hardware or software is properly installed. If this is a new installation, ask your hardware or software manufacturer for any Windows updates you might need. If the problems continue, disable or remove any newly installed hardware or software. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode.

Technical information: *** STOP: 0x000000CA (0x00000001, [PART THAT GOES HERE CHANGES @ EVERY STARTUP], 0x00000000)

The only thing I've done recently is install the K-Lite Codec pack on Windows.

Now I can't boot into Windows at all. I can't boot from the Windows installation CD either - same blue screen every time.

All of the hardware diagnostics come back clean. I tried booting with pretty much everything in the BIOS disabled, only Dell's ram, no optical drive, etc,. I called Dell and they had me repeat everything I already tried, then blamed it on Linux and said I should reformat my entire harddrive.

Ubuntu still works great but my partition table is really confusing me.  I'm wondering if someone can help me interpret this.  In addition to the Windows NTFS partition and dell's 3 vfat partitions, I created ext3 /, ext3 /home, and linuxswap.

I'm wondering if I have too many partitions and that's what is causing Windows to die.  Also, when I run GParted (I wanna wipe out all non linux partitions) it just shows the entire disk as unallocated!! 

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           13727       13987     2096451    c  W95 FAT32 (LBA)
/dev/sda2   *           7        3654    29302560    7  HPFS/NTFS
/dev/sda3            3655       13987    82999822+   f  W95 Ext'd (LBA)
/dev/sda4           13988       14593     4867695   db  CP/M / CTOS / ...
/dev/sda5           13727       13987     2096451   dd  Unknown
/dev/sda6            3655        6086    19534977   83  Linux
/dev/sda7            6087       13599    60348141   83  Linux
/dev/sda8           13600       13726     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks for any tips!!

---

### Post by jvc26 on 2007-02-10
Can I ask what these two are?:
/dev/sda4 13988 14593 4867695 db CP/M / CTOS / ...
/dev/sda5 13727 13987 2096451 dd Unknown
The 0x000000CA error has something to do with plug and play drivers by the looks of this:
[http://msdn2.microsoft.com/en-us/library/ms795954.aspx](http://msdn2.microsoft.com/en-us/library/ms795954.aspx)
STOP codes occur when the windows loading is stopped, due to a whole possible range of errors. I used to get stops when I had RAM issues, but they appear to be caused by a whole possible bunch of things.
I very much doubt its linux's fault; I'm just wondering - those arent all primary partitions are they? I didnt think it was possible to set up more than 4 primaries on a drive?
Il

---

### Post by amir.khosroshahi on 2007-06-09
Hi,
I have just the same problem as you, and my system is a Dell Inspiron 6400 laptop, with the same Media Direct stuff...
In my case, it happened just after I used S-video in Windows to connect the laptop to a TV. But I don't know if that is really the cause.
Another thing that I suspect is that when I log in to Gnome, it gives a warning about a keyboard layout mismatch between X Window System and Gnome, which did not appear before.
Does it show up in your case?

---

### Post by rocketscientistnot on 2007-09-22
I recently suffered the same problem.  When I installed Ubuntu a few months back, I accidently wiped out my drive.  So I reformatted, and created partitions for XP and Linux.  I assumed I had removed any of the other things Dell put on the HDD.    I was finally able to get my dual boot situation working.  Until the other day, when I hit the Media Direct button.  I got the blue screen telling me that Windows had shut down and a STOP: 0x000000CA message.  I can no longer boot into XP, though Ubuntu still works fine.   I've since learned from this forum that the Media Direct button can wreak havoc with your system if it's not configured the way Dell intended.  My question is...What Now?  Can I recover?  Or must I back up my data and start all the way over?  I believe I have the Media Direct disk to install if I want to.

---

### Post by pmoseley on 2007-09-22
The easiest option in my opinion for a dual booting system on a DELL laptop is to:

1) Delete Windows partition
2) Create Windows partition (smaller so you have enough room for linux partitions)
3) Reinstall windows using an origonal XP disk (not the recovery disks which contain all the crap DELL system software)
4) Install Ubuntu in the now free space (from deleting the old windows partition and making a smaller one.

Remember linux ideally needs a swap partition!

---

### Post by myxolam on 2008-07-03
I got this exact problem today (I can boot into Ubuntu, but get the error that antihero gets when I go into windows), and I remember this began after I mistakenly hit the media direct button. 
(dual boot Ubuntu and xp). I cant even use driveImage to restore the windows partition.
 Did anyone solve this problem....hopefully, I dont have to do a reinstall. Before this happened today, I had been running dual boot for about 3 months happily.
Here is my current partition setup.

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1           14268       14593     2618563+   c  W95 FAT32 (LBA) 
/dev/sda2   *          11        7973    63962797+   7  HPFS/NTFS 
/dev/sda3            7974       14593    53175150    f  W95 Ext'd (LBA) 
/dev/sda5           14268       14593     2618563+  dd  Unknown 
/dev/sda6            7974       14004    48443944+  83  Linux 
/dev/sda7           14005       14267     2112516   82  Linux swap / Solaris 

not sure where media direct is located... maybe in f W95 partition?
THis is a dell vostro 1700.
Thanks

---

