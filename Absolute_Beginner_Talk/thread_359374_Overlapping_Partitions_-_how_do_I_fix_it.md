---
title: "Overlapping Partitions - how do I fix it"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Psquared on 2007-02-11
I'm not an absolute beginner, but i feel like it tonight. I do not currently have windows on this box. I did have Vista RC1. I'm pretty sure that is where the overlapping came from.

Here is my output from fdisk -l

> 
Device         Boot           Start            End           Blocks           Id            System
/dev/hda1                            1           4742       38090083+     83            Linux
/dev/hda2      *              9374         13628       34178287+     83            Linux
/dev/hda3                    13629         19457       46821381+       5            Extended
/dev/hda4                      4743           9373       37198507+     83            Linux
/dev/hda5                    19270         19457         1510078+     82            Linux swap
/dev/hda6                    13629         19269       45311269+     83            Linux
/dev/hda7                    13629         13629                     0+     83            Linux
/dev/hda8                    19270         19270                   31+     83            Linux


I have Fluxbuntu on hda1. It runs fine. I have Elive on hda2 (root-boot) and it runs fine. I have installed VL5.8 (Vector Linux) on hda4. It will run, but has some problems. As you can see these partitions are not in order and there is some overlap with the swap on hda5 and the extended partition on hda3. In addition, I don't need the other three partitions. (6, 7 & 8) and I don't know how they got created.

Gparted will not run so whatever changes I make will have to made using the CLI. What I want to do is save hda1 and hda2, and have a larger partition for swap. The rest I want to just delete and have as contiguous unallocated space. Maybe we could expand hda1 to 9373 (the current end of hda4) and make it boot/root??:guitar: 

The reason is I don't like leaving a mess behind ... plus, I want to try a couple of new distros so i will create partitions in that space at a later time. (Dreamlinux in particular i want to try, and maybe Vector again or Zenwalk. I don't think this is Vector's fault.

So, could someone walk me through the steps to do this. You know, First, then Second, then third ... etc. Fluxbuntu contains my email which I don't want to lose so whatever we do I can't muck up hda1 and hopefully not hda2. :lolflag: 

Thanks in advance.

---

### Post by Psquared on 2007-02-12
Nobody has any ideas on this one??

---

### Post by Psquared on 2007-02-13
back to the top - I really need help with this.

---

### Post by housam on 2007-02-13
Try to edit your fdisk -l using [this guide ]("http://community.linux.com/howtos/Partition/fdisk_partitioning.shtml"). specially parts 5 & 8.

---

### Post by mixmaster on 2007-02-13
To be honest, that partition table looks distinctly dubious.  The fact that gparted will not run is also not a good sign.

Before you do anything you should back up any data you cannot afford to lose.  Then I would use fdisk to delete hda7 & 8 as they seem to be overlapping other partitions.  Then try gparted again and see if it will run now.

Alternatively, you could try some commercial software.  I used to use Partition Magic, but it is no longer available and to be honest could sometimes make the situation worse when confronted by a bad partition table.  More recently, I have had some success with Acronis partition manager, which will work on the more common linux file systems but you would need a windows box to build the self-booting CD which it uses in standalone mode.

---

### Post by Psquared on 2007-02-15
I was able to delete the partitons 4-8 as well as 3. (they are not in order) gparted will run, but it shows the unallocated spaces between hda1 and hda2 as hd-1. After hda2 the remainder of the unallocated space is also shown as hd-1. My system boots fine, but I'd like to make the partitions more "logical" in the sense that hda1 and hda2 are continguous. I assume I need to enlarge both, but gparted will not let me do that. I can't change the partition size.

I'm going to try the Linux Gparte Live CD and see if it can do it.

Right now, fdisk -l only shows hda1 and hda2 with hda2 as boot/root/primary.

---

### Post by omrojas on 2007-02-24
Hello, I'm having the same overlapping partition problem that doesn't allow me to use gparted, or boot into Windows.

I will explain the problem from the beginning: 

I have a Dell Inspiron 6400 running both XP Pro, and Ubuntu Linux. Yesterday, by mistake I turned on my laptop not using the power button but the button used for Media Direct. It came with a BSOD  saying that the plug and play module could not load probably caused by a faulty driver. After that i haven't been able to boot into windows. Every time i try the BSOD comes up.

I tried checking the partition tables with fdisk -l and noticed overlapping particions

fdisk -l shows this:

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1           18689       18949     2096451    c  W95 FAT32 (LBA)
/dev/sda2   *           7       11325    90919867+   7  HPFS/NTFS
/dev/sda3           11326       18949    61239780    f  W95 Ext'd (LBA)
/dev/sda4           18950       19457     4080510   db  CP/M / CTOS / ...
/dev/sda5           18689       18949     2096451   dd  Desconocido
/dev/sda6   *       11326       18385    56709387   83  Linux
/dev/sda7           18386       18688     2433816   82  Linux swap / Solaris

any hints in how to fix it without having to reinstall/format??

---

