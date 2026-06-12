---
title: "Ubuntu 10.10 Boot Problems"
date: 2010-10-10
forum: Apple Hardware Users
---

### Post by rhcp1253 on 2010-10-10
After numerous tries with installation, i finally managed to get ubuntu installed on my **Macbook Unibody 5,1**. I deleted my Ubuntu Studio 10.04 install with gparted, then restored my Partition Map with Boot Camp Assistant. I then repartitioned my HD with Boot Camp Assistant, and booted from the ubuntu live cd. I deleted the bootcamp partition with gparted, and went on with the install. I was expecting to see an "Largest continuous free space" option, but ignoring that missing option, i chose to specify manually. I made an Ext4 Partition, and a Swap in that free space, and installed grub2 to /dev/sda3, the ext4 partition. All seemed well, until i booted. **Mac OS boots fine, but when i boot linux with rEFIt or the normal EFI, it displays some strange character, and hangs**. That or it just hangs at a flashing prompt. I'm very confused, and would appreciate any help. Thanks in advance :)

---

### Post by tpievila on 2010-10-11
What boot options does rEFIt give you? Does it recognise your Ubuntu as Linux, or just as "Legacy OS? Please post your GPT and MRB tables (you can use "gdisk /dev/disk0" in OS X, then press r to go to rescue mode, press p to print your GPT and o to print your MBR).

---

### Post by rhcp1253 on 2010-10-11
This is what i got from Partition Inspector
```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    434520103  Mac OS X HFS+
 3      434522112    482537471  Basic Data
 4      482537472    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    434520103  af  Mac OS X HFS+
 3 *    434522112    482537471  83  Linux
 4      482537472    488396799  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: GRUB
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 434522112:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 482537472:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

```

---

### Post by rhcp1253 on 2010-10-11
And it shows up as "Legacy OS"

---

### Post by tpievila on 2010-10-11
While I'm not completely sure about this, I think that GRUB either requires a real MBR system, or a special partition called "BIOS boot" ([http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)). The problem is that GRUB usually installs itself to 62 sectors that come right after the MBR, but on GPT systems this part contains the GPT header.

When I installed Ubuntu, this was automatically created for me, though I'm not sure if I needed to check a setting or something. Also that was 10.04.

What you need to do, is to repartition a small extra partition, easiest would be to take it from your swap. See the grub-documentation I linked earlier. Then you need to boot into a Linux system (most likely with a live cd) and reinstall grub to /dev/sda. That should put the stage 1 into MBR and stages 1.5/2 onto the special partition. Works fine here.

---

### Post by rhcp1253 on 2010-10-11
Won't installing grub to /dev/sda nuke my hard drive? I think that's how I screwed up my last install, and destroyed my partition map

---

### Post by tpievila on 2010-10-12
> **rhcp1253 said:**
> Won't installing grub to /dev/sda nuke my hard drive? I think that's how I screwed up my last install, and destroyed my partition map

Please read the linked GRUB documentation. If the partition table includes the BIOS boot partition, GRUB will notice it and instead of writing to just after the MBR part, will write it's 1.5 and 2 stages to that special partition.

---

### Post by srs5694 on 2010-10-12
Two comments:

First, on a GPT or hybrid MBR disk, GRUB should *not* damage GPT data structures; it should install to the BIOS Boot Partition, as tpievila says, or use a hard-coded sector list. On a BIOS-based system, GRUB will install its first stage to the MBR. It appears from [this page](http://grub.enbug.org/TestingOnEFI) that the commands to install GRUB 2 on a Mac are very different from the commands to install it on a BIOS-based system; there's no need to write to the MBR at all. I must emphasize that I don't own an Intel-based Mac and so haven't tested this.

Second, you can add a measure of safety by backing up your partition tables. My [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program has an option to do this: It's "b" on the main menu. Create a backup file (say, partitions.gpt) and copy it to a USB flash drive or some other safe location off the hard disk. Then if you have problems, you can boot an emergency disc and restore the partition table. The restore function is on the recovery & transformation menu; you'd type "r" to get there, then "l" (lowercase L) to load the backup file, and then "w" to save it back out. The backup created by GPT fdisk includes the protective or hybrid MBR, the main and backup GPT metadata, and one copy of the partition table (which is identical in main and backup form on a healthy disk). Restoring a backup restores all of these items (copying the partition table to both its main and its backup locations).

---

### Post by rhcp1253 on 2010-10-12
So, how should i proceed?

---

