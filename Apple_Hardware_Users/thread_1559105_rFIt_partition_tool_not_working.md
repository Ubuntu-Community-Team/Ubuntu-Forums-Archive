---
title: "rFIt partition tool not working"
date: 2010-08-23
forum: Apple Hardware Users
---

### Post by MacAodh on 2010-08-23
Hi all,

I installed Ubuntu as shown in the wiki and when I went to restart it gave me a lovely blinking cursor and nothing else. So I held down option, loaded into osx, reinstalled rEFIt and got my menu on startup.

Unfortunately, the partition sync tool doesn't seam to be working, it gives me an error:

Status: MBR partition table is invalid, partitions overlap.
Error: Not Found returned from gptsync.efi

*hit any key to continue*

Any suggestions???

---

### Post by MacAodh on 2010-08-23
Anybody??? Somebody???

---

### Post by dngfng on 2010-08-23
Can you also let us know what mac you are trying to install to?

Also just to make sure you followed the steps:

1. Installed rEFIt from OSX
2. Repartitioned the drive (i.e. added extra partions for root and swap).
3. Started up and installed Ubuntu via selecting Ubuntu from CD in the rEFIt boot menu.
4. installed ubuntu

Just in case, I went via the installation instructions hear:
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

Worked well.

---

### Post by MacAodh on 2010-08-23
1st gen macbook.
I used bootcamp to partition the drive then installed ubuntu

---

### Post by srs5694 on 2010-08-23
> **MacAodh said:**
> Unfortunately, the partition sync tool doesn't seam to be working, it gives me an error:

Status: MBR partition table is invalid, partitions overlap.
Error: Not Found returned from gptsync.efi

*hit any key to continue*

Any suggestions???

Your Master Boot Record (MBR) partition table is corrupted. Chances are it's the same issue (albeit not the same symptoms) described in [this thread.](http://ubuntuforums.org/showthread.php?t=1556993) See my post there (#8 in the thread) for a solution. If you need verification, post the output of the "sudo fdisk -l" text-mode command for us to examine.

---

### Post by MacAodh on 2010-08-23
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        7206    57671680   af  HFS / HFS+
/dev/sda3               1        7206    57878527+  ee  GPT
/dev/sda4            7206        9619    19383296   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

Going try your solution but in the meantime, me thinks that's what your after... I hope

---

### Post by MacAodh on 2010-08-23
Okay, I think I see whats going on, my old sda3 is overlapping sda1&2. So need to get rid of that. Can I use gparted for that or do i need to/should i use fdisk?

Also, I've no idea what a hybrid mbr is... Do i have one/should i get rid of it?

Sorry for being thick, this is what happens when i need a new laptop but can't aford a macbook next & need to try out ubuntu...

---

### Post by srs5694 on 2010-08-23
Yes, your MBR is fubared. It's a hybrid MBR -- anything with a type-0xEE partition and anything else is a hybrid MBR. If it's got a single 0xEE partition, it's a conventional protective MBR, which is part of a standard GPT disk. If it's got one or more MBR partitions and *none* of them has a type code of 0xEE, it's a plain MBR disk without GPT. Hybrid MBRs are [ugly and dangerous.](http://www.rodsbooks.com/gdisk/hybrid.html) Yours is messed up because it's got two 0xEE partitions and one of them overlaps with two other partitions. Hybrid MBRs are *not* necessary to dual-boot Linux and OS X. They're most commonly employed in Windows/OS X dual-boot configurations, either when using Apple's Boot Camp or when creating a Hackintosh (OS X on commodity PC hardware).

You can get rid of the MBR's /dev/sda3 by using Linux's fdisk. This will leave you with a hybrid MBR, but it will be functional (I wouldn't say "legal," since hybrid MBRs violate the GPT specification). *Do not* use GParted. Although I've seen one report of somebody fixing this type of problem with GParted (or maybe it was GNU Parted; both are based on libparted), that's a risky approach, since there's no telling whether a libparted-based tool will edit the MBR side or the GPT side. You want to leave the GPT data structures alone and only remove that errant MBR /dev/sda3. I can't tell from what you've posted what the GPT-side /dev/sda3 is; it could be important.

If you want to go to a straight protective MBR, you can use [GPT fdisk's](http://www.rodsbooks.com/gdisk/) gdisk program (without using Linux fdisk):

```

$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.6.10

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): x

Expert command (? for help): n

Expert command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.
$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.6.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 31576064 sectors, 15.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 479B9C0C-49A7-4DBD-B555-129862C516EC
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31576030
Partitions will be aligned on 1-sector boundaries
Total free space is 13690 sectors (6.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63         8080127   3.9 GiB     0700  Linux/Windows data
   2         8080128        16160255   3.9 GiB     0700  Linux/Windows data
   5        16160319        24240383   3.9 GiB     0700  Linux/Windows data
   6        24240447        31562495   3.5 GiB     0700  Linux/Windows data

```

The "n" option on the experts' menu creates a fresh protective MBR, and "w" saves the changes (in this example, just creating that new protective MBR). The second launch of gdisk verifies that this change took place; note the changes in the partition table scan on the two launches in this example.

If you wipe the hybrid MBR in favor of a protective MBR, it's conceivable you'll need to re-install your boot loader. I'm not positive of that, though; I don't know enough about rEFIt to know how it would react to this change.

If you can't currently boot Linux, you'll need to make these changes from an emergency boot disc or from OS X. (GPT fdisk is available for OS X.)

---

### Post by MacAodh on 2010-08-24
Unfortunetly I wasn't patient enough to wait for your reply so I used gparted, deleted sda3 and then used fdisk as you recomended. Now rEFIt is comming up, I'm sellecting ubuntu but it's hanging on a blank screen afterwards so i'm thinking i might have to re-instal the boot loader. How do you do this?

I've posted the output of sudo fdisk -l just to make sure i've done good. Thanks a million for the help again

```
 WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        7206    57671680   af  HFS / HFS+
/dev/sda3            7206        9619    19383296   83  Linux
/dev/sda4            9619        9730      888832   82  Linux swap / Solaris

```

---

### Post by srs5694 on 2010-08-24
Your fdisk output shows a reasonable hybrid MBR. As to the rest, I'm not very familiar with rEFIt, so I'm afraid I can't offer more advice. With any luck somebody else will be able to guide you through to get a bootable system.

---

### Post by kennethsime on 2010-08-24
Hey, we had a super similar problem, and this is how I fixed mine: 
[http://ubuntuforums.org/showthread.php?p=9762055#post9762055](http://ubuntuforums.org/showthread.php?p=9762055#post9762055)

I ran the gdisk tool to create a "protective" MBR, which shows only a single partition spanning the whole drive labeled "GPT". From here what worked for me was just using rEFIt's partitioning tool, otehrwise known as GPTSYNC, which writes a new MBR table based on your GPT table. Ubuntu will use this new MBR table to figure out where to boot from. Or something like this.

---

