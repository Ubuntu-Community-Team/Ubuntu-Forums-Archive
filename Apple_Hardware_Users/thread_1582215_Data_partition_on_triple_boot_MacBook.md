---
title: "Data partition on triple boot MacBook?"
date: 2010-09-26
forum: Apple Hardware Users
---

### Post by vmorley on 2010-09-26
Hello all,

I have just set up a MacBook Pro (version 7.1) to triple boot with Snow Leopard, Ubuntu 10.04 and Windows 7, using the Refit boot manager. Everything is working perfectly, so naturally I can't leave well enough alone.

I'd like to set up a data partition to keep all my files in one place. It would be easier to find them, easier to make back-ups, and avoid the risk of losing data if I have to reinstall an OS.

The problem is that the hard disk already has four primary partitions (one for each OS and the EFI partition which Mac OS seems to require). I understand that Windows won't work with more than four primary partitions, and that the others won't recognise extended partitions, so I don't know if it is possible to set up a data partition as I would like.

I would be grateful if anyone could advise me.

---

### Post by srs5694 on 2010-09-26
You're under a dangerous misconception -- or at best a partial conception. Out of the box, an Intel-based Mac starts with a [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) configuration, which makes no distinction between primary, extended, and logical partitions. GPT can support 128 partitions by default, although that value can be changed with the right software.

Unfortunately, Windows has only middling GPT support at best, and some versions have none at all. Thus, to get their Macs to dual-boot, Apple resorted to an ugly, flaky, and even downright dangerous hack called a [hybrid MBR.]("http://www.rodsbooks.com/gdisk/hybrid.html") In this configuration, the "protective MBR" of GPT (which exists to keep GPT-unaware utilities from messing with a GPT disk) is co-opted to include up to three MBR partitions that point to real GPT partitions. The fourth MBR primary partition is required to flag the disk as having GPT data. This is what you've got now. Windows give precedence to the MBR when it finds a hybrid MBR disk, so Windows can see up to three partitions. OS X and Linux, OTOH, give precedence to the GPT data, so they can see all the partitions on the disk.

In theory, you should be able to get a working system, including a shared data partition, by removing either the OS X or the Linux partition from the hybrid MBR and substituting the shared-data partition. Both OS X and Linux are quite happy to boot from GPT-only disks and will ignore the MBR data in a hybrid MBR. You can reconfigure your hybrid MBR using my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") utility, which is available for all three of the OSes you're using. Go to the recovery & transformation menu, type "p" to see your current partitions, and then type "h" to create a new hybrid MBR. You'll be asked for partition numbers and for information about the partitions. When you're done, type "w" to save your changes and exit. You'll need to do this after you resize your partitions to create the new shared-data partition.

That said, there's one key element about which I'm unclear: I don't know what the rEFIt boot loader's requirements are. If rEFIt relies on the MBR, you might have trouble getting the OS that you remove from the hybrid MBR to boot, although I can think of several possible workarounds (like storing the Linux kernel and initrd image on the OS X partition and ensuring it's in the MBR).

Note that resizing your partitions could disrupt your hybrid MBR configuration. I recommend you do this:


[LIST=1]
[*]Use Linux fdisk to view your current hybrid MBR, as in "sudo fdisk -lu /dev/sda". Make a hardcopy of the output, and mark each partition for its role, if necessary (as in "OS X boot partition"). This will enable you to recreate something that matches, if necessary.
[*]Resize your partitions and create the new shared-data partition. I'm guessing you'll use OS X's Disk Utility and/or GParted in Linux to do this. *Do not* use a Windows utility for any part of this; the Windows utility will only see the MBR side of the disk, which has incomplete information, so using Windows for partition resizing will likely create a tangled mess of MBR-GPT inconsistencies. (This is one of the many reasons why hybrid MBRs are so dangerous; it's too easy to make this sort of mistake if you're not very well informed!)
[*]Repeat step #1. It's possible that one or more of the hybridized partitions will be missing or changed.
[*]If any of the original hybridized partitions is now missing from the MBR, use gdisk to create a fresh hybrid MBR that matches the original in terms of which OS's boot partitions are present.
[*]It may be necessary to re-install rEFIt at this point, but I'm not positive. You could just try it, or you could read its documentation to try to figure out its requirements.
[*]To be safe, if you re-installed rEFIt, repeat step #1. If rEFIt installation disrupted the hybrid MBR configuration, use gdisk again to fix it.
[*]Reboot and test all three OSes' ability to boot, keeping your fingers crossed the whole time.
[/LIST]


If you can't boot the OS that you removed from the hybrid MBR, you should be able to use gdisk to add it back (removing the shared data partition in the process), at least temporarily. You might then be able to experiment with GRUB 2 instead of rEFIt or try a workaround like moving the Linux kernel and initrd onto the OS X or Windows partition and re-writing the boot loader rules to look for them there.

---

### Post by vmorley on 2010-09-26
Many thanks for a very full and informative answer. I appreciate the trouble you took.

I'll definitely try your gdisk utility, but I think I'll wait until next Saturday to do so because it sounds like I might need an all day session to get things working (or to restore everything to the starting point if I mess up). I'll report back on how it goes.

At present, I have five years of data from my old laptop (a dual boot PC running Windows XP and Hardy Heron) on an external hard disk that all three OSs on the MacBook Pro can access. It isn't an ideal solution, but I could live with it if I have to.

Vincent Morley

---

### Post by coiske on 2010-11-17
Just started looking into this, as I'm about to implement the same sort of thing. It sounds like Grub might actually have to be on one of the first four partitions in order for it to successfully boot Linux.  (srs5694, correct me if I'm wrong.)   You could accomplish this by making partitions 2-4 your Linux, Windows, and Data partitions, and partition 5 your MacOS partition. (And installing Grub to your Linux partition.)

I'm not crazy about this solution. I was under the impression that earlier partitions are toward the outer rim of the drive, leading to faster seek times. So I really wanted MacOS to be my second partition, rather than my fifth. But it looks like I may have to bite the bullet and put the MacOS partition fifth.  Let me know if you come up with a better solution, though.

---

### Post by srs5694 on 2010-11-17
> **coiske said:**
> Just started looking into this, as I'm about to implement the same sort of thing. It sounds like Grub might actually have to be on one of the first four partitions in order for it to successfully boot Linux.  (srs5694, correct me if I'm wrong.)   You could accomplish this by making partitions 2-4 your Linux, Windows, and Data partitions, and partition 5 your MacOS partition. (And installing Grub to your Linux partition.)

The question of where GRUB resides is much more complex than you seem to understand. GRUB consists of several components, each with a different location:


[list]
[*]The optional GRUB first-stage loader resides in the MBR.
[*]Additional code (sometimes referred to as "stage 1.5") resides in unallocated space after the MBR on MBR disks or in a dedicated partition on GPT disks. This code need not always be present, depending on the configuration.
[*]GRUB code may sometimes be installed in the boot sector of a partition, typically the Linux root (/) or /boot partition, although other partitions are possible homes for this code.
[*]On a true EFI system, GRUB can place an EFI file in the EFI System Partition (ESP), where it can be found by the standard EFI boot loader or by a secondary EFI boot loader, such as rEFIt.
[*]GRUB boot-time configuration files reside in the /boot/grub directory, which can be on the Linux root (/) partition or on a separate /boot partition. Some exotic (by conventional Ubuntu standards) installations can place these files elsewhere.
[*]GRUB system configuration files reside in /etc/grub.d. These files aren't accessed at boot time; they're used by GRUB system utilities for maintaining GRUB.
[*]GRUB system utilities reside in /usr/sbin, or perhaps elsewhere. These files aren't accessed at boot time; they're the utilities that install and maintain GRUB.
[/list]


A default Ubuntu installation typically places GRUB code in the MBR and then relies on the post-MBR or dedicated-partition code and files in /boot/grub during the boot process, so in some sense GRUB is "installed" to all three of those locations. It's possible to put GRUB on the boot partition, though, leaving the MBR to house a Microsoft-style boot loader.

On a Mac, this is all complicated by Mac-specific quirks. The Mac's firmware enters a BIOS emulation mode when it sees MBR partitions, and a standard Ubuntu install relies on this to get GRUB to work. Nonetheless, this can be a flaky approach. You might conceivably have better luck by uninstalling grub-pc and installing grub-efi, which installs a slightly different version of GRUB that uses the ESP-based file instead of MBR-based code. I've done some experimentation with this approach myself, and with good results; however, I've only used this with a dual-boot configuration (Linux and OS X) with a pure GPT that lacks the ugly and dangerous hybrid MBR that's required to boot Windows on a Mac.

> I'm not crazy about this solution. I was under the impression that earlier partitions are toward the outer rim of the drive, leading to faster seek times. So I really wanted MacOS to be my second partition, rather than my fifth. But it looks like I may have to bite the bullet and put the MacOS partition fifth.  Let me know if you come up with a better solution, though.

It's not the seek times that are affected; it's the transfer rates. In theory, these will be faster for partitions on the outer rims of the disk, since more sectors pass under the drive's head for each rotation of the disk. In my experience, the faster sectors are sometimes at the start and sometimes at the end of the disk. I just ran some tests, and a 2.5-inch 60 GB SATA drive in a Mac Mini had 25% faster access near the end of the disk, but a 3.5-inch 320 GB PATA drive in a PC had 50% faster access at the start of the disk. If you're concerned about that sort of performance effect, you should test your disk before laying out partitions. Keep in mind, though, that even a 50% speed difference in a disk-intensive benchmark is likely to translate into barely-noticeable effects in the real world, since other factors (such as disk caching and CPU speed) will enter into the equation.

Also, the location of a partition's sectors on the disk is completely unrelated to the location of the partition's definition in the partition table. Partition #1 could be the last one on the disk in terms of sector placement, partition #2 could be the first, and partition #3 could come in-between them. Further complicating things is the fact that you're talking about a hybrid MBR, which has *two* partition tables, and the GPT and MBR partitions need not coincide in order. This is very confusing, but it also means you can lay out your partitions to optimize performance and then assign them whatever numbers are necessary for your task, particularly with respect to getting the desired partitions into the hybrid MBR.

---

### Post by Ritzbitts on 2011-09-09
Ok, so I can follow the process for rewriting the hybrid MBR in theory, but in terms of using gdisk, I get a little lost. This is the result of fdisk after creating and resizing everything:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06db542e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2          409640   117597143    58593752   af  HFS / HFS+
/dev/sda3       117860352   179301464    30720556+   7  HPFS/NTFS
/dev/sda4   *   459716040   480198914    10241437+  83  Linux

```

Now, can see where the "unallocated" ext2 partition is between sda3 and sda4. I understand that, in order to get the partition to be recognized in Windows and still have Ubuntu bootable, I have to remove sda2 from the Hybrid MBR so it reads as "unallocated," and add an entry for the ext2 partition. I have done these kinds of things in the past with sfdisk do fix faulty MBRs, but I'm not sure I understand the process with gdisk enough to plunge in. Now that I have everything properly partitioned in Ubuntu, I assume I have to start form a liveCD, run gdisk on sda, and just use the d, n, and w commands? What exactly will this entail?

Linux and Mac read the disk as having the 200MiB EFI partition, a 55.88GiB HFS+ partition, 128.52MiB of unallocated space, 29.3GiB NTFS partition, 133.71GiB Ext2, 9.77GiB Ext4, and 3.91GiB Swap.

I'm sorry to bother people for this, but I want to make sure I have it right before I dig myself a hole. Once I get it done I intend to write a guide and/or update the Ubuntu documentation for triple boot setups.

Thanks in advance!

---

### Post by srs5694 on 2011-09-09
> **Ritzbitts said:**
> Ok, so I can follow the process for rewriting the hybrid MBR in theory, but in terms of using gdisk, I get a little lost.
...
I understand that, in order to get the partition to be recognized in Windows and still have Ubuntu bootable, I have to remove sda2 from the Hybrid MBR so it reads as "unallocated," and add an entry for the ext2 partition.

It's unclear what you mean by "the partition" in "...in order to get the partition to be recognized...." Normally, you only need Windows partitions in a hybrid MBR, since Windows is the OS that uses the MBR side of a hybrid MBR configuration -- Linux and OS X both read the GPT side.

The gptsync tool does an adequate job of setting this up in some simple configurations, but if you need more flexibility, gdisk does a better job. See [its Web page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) for detailed usage instructions. You can place up to three GPT partitions in the hybrid MBR, so select whichever ones you want to see in Windows.

> I have done these kinds of things in the past with sfdisk do fix faulty MBRs, but I'm not sure I understand the process with gdisk enough to plunge in. Now that I have everything properly partitioned in Ubuntu, I assume I have to start form a liveCD, run gdisk on sda, and just use the d, n, and w commands? What exactly will this entail?

gdisk is fundamentally a *GPT* tool, and its "d" and "n" main-menu commands affect *GPT* partitions. If the partitions are already properly defined on the GPT side, you should *not* use those commands, since doing so will, at best, put you back where you started and, at worst, trash your partitions. You should, instead, type "r" to go to the recovery & transformation menu, followed by "h" to create a hybrid MBR. Once you've done that (which involves answering several questions), you can type "w" to save your changes. Again, see the [GPT fdisk hybrid MBR page](http://www.rodsbooks.com/gdisk/hybrid.html) for details.

---

### Post by Ritzbitts on 2011-09-14
Thanks for the fast reply! The link you provided was very helpful, as was Gdisk. I found it very powerful, and very easy to use. After some experimentation (that is, trial and error), I configured the hybrid MBR so that Windows would recognize the shared Ext2 partition, my Linux boot partition was still bottable through rEFIt, and there were no problems with Mac OS. It was simple to do, all it required was removing the MAC HD from the HMBR and adding an entry for the data partition.

Oddly, even though Mac and Linux were able to handle everything just fine, Windows took issue with the shared partition. I tried labeling it as "07" and as "83" using Gdisk through a pMagic Live CD, with the same result. Although Windows was able to read and write to external Ext2 drives without incident, it insisted that the internal partition required formatting before it could be read. After trying everything I could think of, I threw my hands up and decided to format the partition as NTFS.

This is where I made a huge mistake. I didn't follow your advice to never let Windows touch my partitions, and instead of using Gparted, I did a quick format through Windows. Bad move! This resulted in both Windows and Linux being unbootable through rEFIt (or otherwise), a very (very very) slow boot for Mac OS X, and a general sense of dread. I used Gdisk to restore the HMBR to its previous state, but to no avail. Even reformatting the data partition back to Ext2 with Gparted and then restoring that HMBR failed to rectify the problem.

After completely wiping the drive and reinstalling all three OSes, I have things set up so that Mac and Linux share an Ext2 data partition with read write access (requires modification to the MacFUSE scripts), and Windows is in its own little bubble. I'd like to give Windows write access to the partition, but it is not absolutely necessary as both Mac and Linux have read write access to NTFS (and despite popular opinion, Mac OS 10.6 and up has native write support for NTFS with minimal scripting, but I digress).

So I'm prepared to try this again, now that I've learned the hard way not to let Windows touch my partitions. But if you have any input on why Windows wouldn't recognize my Ext2 partition while still having full access to external Ext2 drives, I would greatly appreciate it. It was fully visible to the OS, so my guess is I did something wrong when I formatted it, or when I rewrote the HMBR.

Thanks in advance!

---

### Post by srs5694 on 2011-09-14
> **Ritzbitts said:**
> if you have any input on why Windows wouldn't recognize my Ext2 partition while still having full access to external Ext2 drives, I would greatly appreciate it. It was fully visible to the OS, so my guess is I did something wrong when I formatted it, or when I rewrote the HMBR.

I'm afraid I know very little about ext2/3/4fs drivers for Windows, so I'm not sure what caused that problem.

I do want to comment on another point you made in passing, though:

> despite popular opinion, Mac OS 10.6 and up has native write support for NTFS with minimal scriptingI don't know what the state is in OS X 10.7, but in 10.6, the NTFS write support is disabled because it's buggy. I've seen several posts from people who've tried it and who end up trashing their disks as a result. Therefore, I recommend using another solution, such as the NTFS-3g in MacFUSE, instead. (That said, I've never actually trashed a disk myself with the OS X NTFS write support -- but I've never used the driver in write mode!)

---

