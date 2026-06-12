---
title: "dual boot, partitions, mounting hdd"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by IainT on 2006-05-09
I used - [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) - to set up a dual boot system with XP and Ubuntu. 

Problem 1 is that the partitions don't appear to be mounted on the desktop or in /media. The partitions are set-up as recommended (except that I went with 15gb per OS, a 2gb swap file and 48gb left over) Booting into windows doesn't find the 48gb partition, only it's own 15gb partition and what is presumably the 15gb linux partition. 

sudo nano /etc/fstab gives:

/dev/hda3 /ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdd/media/cdrom0 ......

There is more that is related to cdroms and floppies. Apologies if the formatting is weird, it's not copy and paste, I'm using another computer as Ubuntu is not yet online (RaLink 2500 card to figure out later)

Problem 2 is that now when I boot into XP it doesn't recognise my USB mouse and I have to unplug it and plug in it again. That's minor though :)

---

### Post by phatdad on 2006-05-09
Hi there
I'm a newbie, waiting for a reply on my post. I was reading yours and I think the answer lies in the file table. Windows Xp uses NTFS or something, Ubuntu I think is FAT32. I bet the install has divided your disc up as 15GB NTFS, 15GB FAT32 for ubuntu, and them formatted that extra 48GB as FAT 32 for linux use. I
f you mount the windows drive in Ubuntu you can see your NTFS files, but I don't know how to make windows see FAT32 disc space.

---

### Post by IainT on 2006-05-09
Figured it was going to have something to do with that.

Mount windows - as per this link? - [http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php) 

sudo fdisk -l gives me:

/dev/hda1 * 1 1824 14651248+ 7 HPFS/NTFS (I assume this is XP partition)
/dev/hda2 7865 9729 16675470 5 Extended
/dev/hda3 1825 7653 46821442+ 83 linux (this is the 48gb partition?)
/dev/hda5 7906 9729 14651280 b W95 FAT32 (Ubuntu?)
/dev/hda6 7654 7904 2016094+ 82 linux swap/solaris

The problem here is that the link then tells me to sudo nano etc/fstab and edit the hda1 partition, unfortunately the hda1 partition doesn't show up in the list (as it appears in my first post)

Just a hunch here, but has Ubuntu installed into the 48gb partition? It seems to be the case according to newbie intuition, in which case the error is all mine.

Good thing is that I only installed XP yesterday and right now I'm willing to go back and start over if that is going to be the least hassle.

---

### Post by IainT on 2006-05-09
I temporarily managed to mount the windows partition. I then attempted to mount hda3 and the windows partition disappeared. Going into applications>system tools>system monitor> devices it tells me that I have 42gb free space.

Clearly I have installed Ubuntu into a partition that I didn't intend to. My error.

I'm going to format the hard drive using the WinXP install as NTFS, then install XP. Then I'm going to install Ubuntu partitioning the hard drive as follows:

50gb for XP and XP files as NTFS
28gb for Ubuntu and ubuntu files as FAT32
2gb swap file for Ubuntu

Is that reasonable?

---

### Post by phatdad on 2006-05-09
No idea, but good luck;)

---

### Post by chettyk on 2006-05-09
[QUOTE=IainT]
sudo fdisk -l gives me:

/dev/hda1 * 1 1824 14651248+ 7 HPFS/NTFS (I assume this is XP partition)
/dev/hda2 7865 9729 16675470 5 Extended
/dev/hda3 1825 7653 46821442+ 83 linux (this is the 48gb partition?)
/dev/hda5 7906 9729 14651280 b W95 FAT32 (Ubuntu?)
/dev/hda6 7654 7904 2016094+ 82 linux swap/solaris

Good thing is that I only installed XP yesterday and right now I'm willing to go back and start over if that is going to be the least hassle.[/QUOTE]

From the fdisk output that you have given:
Windows XP is on /dev/hda1
Ubuntu is probably on /dev/hda3
Ubuntu swap is using /dev/hda6

Linux cannot be loaded on FAT or NTFS partitions.

In order to mount the Window partition, have a look at:
[https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29)

The Ubuntu Wiki is an excellent resource for coping with a great many situations.

---

### Post by IainT on 2006-05-09
Thanks. I figured that out and decided to go ahead and do a clean install of XP and then give Ubuntu a 20gb partition and reinstall it.

Finished a while back and it worked. This install automatically mounted hda1 but said I didn't have permissions. I unmounted and remounted it and now I'm all good.

Deal with the network card next I think. Thanks.

---

