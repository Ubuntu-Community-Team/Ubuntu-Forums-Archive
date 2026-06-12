---
title: "can't get linux partition to boot"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by SubZeroGTS on 2007-07-18
So I have 3 hard drives. first drive is two partitions, with 1 primary partition, with a windows boot loader on there.

second drive is an empty 233GB drive.

third drive is another 233GB drive, split into 3 partitions (1 for XP, 1 for Vista, 1 plain...). Windows Vista bootloader is in charge and lets me select XP in the menu whereupon it hands things over to XP's boot.ini.

so i split up the second drive into a primary NTFS partition, a linux-swap partition, and an ext3 partition. i set the ext3 as primary and active as well. i installed ubuntu to that drive. and had it install GRUB to (hd1,1) which should be the second primary (the ext3) on the second hd.

i then, while in the ubuntu live CD, ran this command: "dd if=/dev/hdb3 of=ubuntu.bin bs=512 count=1" and thereafter copied the ubuntu.bin over to C:\ (the empty boot drive with the windows bootloader on there), and added to the end of my boot.ini "C:\ubuntu.bin="Linux Ubuntu"".... so Linux Ubuntu now shows up in my boot menu but when I select it, I get a windows error about a bad 'hal.dll' file... if I set the BIOS to boot to the second hard drive (with the NTFS primary and the ext3 primary/active partition), it gives me an error loading os message.

any ideas?

---

### Post by SubZeroGTS on 2007-07-18
k, i remade the ubuntu.bin file and set it up again. now it just pauses at a blank screen with a blinking cursor at the top left and doesn't do anything. o_0

---

### Post by SubZeroGTS on 2007-07-18
Here's my hd/partition layout:

[http://img182.imageshack.us/img182/4356/hdlayoutaw9.jpg](http://img182.imageshack.us/img182/4356/hdlayoutaw9.jpg)

Tomorrow I'm gonna try deleting all the partitions on Disk 2 and installing Linux using the whole drive and if it boots, shrink the volume later and convert the extra space back into that NTFS partition.

---

### Post by use a name on 2007-07-18
Your method seems quite unorthodox to me, but that might be me... What's in that 512 bytes on a disk device? Why do you put that into a .bin and why would a windows loader therefore boot the os on hdb3?

The strange thing is that grub does not work... Did you install that to the mbr of your second drive?

---

### Post by use a name on 2007-07-18
If this method is about compying the contents of an mbr into some .bin file which can be booted by the windows loader, then you should have grub installed to the mbr of your second drive and copy the first 512 bytes of **/dev/hdb** into that file. Still, I've never seen anything like this, but if this method should work, then I think this might be a step in the right direction.

---

### Post by steve.horsley on 2007-07-18
I'm not familiar with the windoze side, but what you're doing with the grub install looks roughly right to me, but I'm not sure about the partition names. If the three partitions on that second disk are NTFS, swap and ext3 then the partiton you need to install GRUB to is (hd1,2), and then take an image from  /dev/hdb3 (or might be /dev/sdb3).

As a double-check, you could try these two things:

Use a live CD, mount the alleged Ubuntu partition (use these commands):
[B]sudo -i
mkdir /media/hdb3
mount /dev/hdb3 /media/hdb3
ls -l /media/hdb3/boot/grub[/B]
which should show you a list of grubs files, such as stage1, stage2 and menu.lst.

You can also use the command 
**strings ubuntu.bin**
which lists the text strings in the file - "GRUB" should be amongst them.

---

### Post by SubZeroGTS on 2007-07-18
> **steve.horsley said:**
> I'm not familiar with the windoze side, but what you're doing with the grub install looks roughly right to me, but I'm not sure about the partition names. If the three partitions on that second disk are NTFS, swap and ext3 then the partiton you need to install GRUB to is (hd1,2), and then take an image from  /dev/hdb3 (or might be /dev/sdb3).

As a double-check, you could try these two things:

Use a live CD, mount the alleged Ubuntu partition (use these commands):
[B]sudo -i
mkdir /media/hdb3
mount /dev/hdb3 /media/hdb3
ls -l /media/hdb3/boot/grub[/B]
which should show you a list of grubs files, such as stage1, stage2 and menu.lst.

You can also use the command 
**strings ubuntu.bin**
which lists the text strings in the file - "GRUB" should be amongst them.hm, i was under the impression that the syntax for the GRUB install was hd[number-of-drive],[number-of-PRIMARY-partition]

so i used (hd1,1) cuz the linux-swap partition wasn't a primary... maybe i should try a reinstall with (hd1,2) when i get back.

---

### Post by SubZeroGTS on 2007-07-18
> **use a name said:**
> If this method is about compying the contents of an mbr into some .bin file which can be booted by the windows loader, then you should have grub installed to the mbr of your second drive and copy the first 512 bytes of **/dev/hdb** into that file. Still, I've never seen anything like this, but if this method should work, then I think this might be a step in the right direction.that's a good idea too. i should probably have done that since there's no other OS(s) on there.

---

### Post by steve.horsley on 2007-07-18
> **SubZeroGTS said:**
> hm, i was under the impression that the syntax for the GRUB install was hd[number-of-drive],[number-of-PRIMARY-partition]

so i used (hd1,1) cuz the linux-swap partition wasn't a primary... maybe i should try a reinstall with (hd1,2) when i get back.
I'm not sure what you mean by "not a primary partition" - you created an extended partition and placed swawp in there? Extended partitions number from hdb5 (hd1,4) upwards, because 1-4 are the four primaries, even if they have no space allocated.  If you run **gparted** from the live CD, it will tell you what the partitions are and what they're called. You can use gparted to just look at what's there without actually changing anything.

I think the windows bootloader would expect to boot the partition hdb3, not the MBR hdb of the disk - after all, the MBR is where the windows bootloader would normally live. So I think it's the partition you should be imaging, not the MBR.

P.S.
How did you install GRUB in the partition superblock? I've never been able to do that with the "alternate" installer CD - it always fails to install and needs a manual clean-up which I guess didn't happen to you. 
Does the "desktop" live CD installer give you the option? I was under the impression it didn't, so have never looked for it.

---

