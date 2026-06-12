---
title: "Installing Questions (Mac and Partitioning)"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by egarren on 2008-03-17
I have spent hours looking for answers so please help me!! First of all, I have an Apple imac w/ leopard, i partitioned my hardrive to run bootcamp (on 10gb), and I downloaded and burned the ubuntu installer.  I don't have parrallels and don't plan on buying it.  I also don't have an external hardrive, so I can't back up my 100gb of data.  So, I want to install ubuntu on the pc partition of my hardrive without deleting any of my stuff.  I have read lots of horror stories about people erasing their entire computer.  Can I just select "Manual" on the ubuntu partition screen and then check the box next to the 10gb partition?  Thanks!

---

### Post by cj2003 on 2008-03-17
There's an explanation in ["How To Dual Boot Ubuntu Gutsy And Mac OSX Leopard 10.5.1"]("http://ubuntu-news.net/modules/news/article.php?storyid=4139")

---

### Post by egarren on 2008-03-17
Thank you, but I still have one pressing issue.  What should I do about partitioning?  I already have a partition, and I don't want to lose any data.

---

### Post by jken146 on 2008-03-17
You might want to post the output of ```
sudo fdisk -l
``` so we can clearly see exactly how your partitions stand atm.

You can use the manual partitioning option, yes, and 10 GB should be ample for Ubuntu's root (/).  You'lll also want a swap partition, up to a gig in size.  Format the root partition as ext3 and choose / as its mount point.

---

### Post by egarren on 2008-03-17
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
	-i: initialize disk with new MBR
	-u: update MBR code, preserve partition table
	-e: edit MBRs on disk interactively
	-f: specify non-standard MBR template
	-chs: specify disk geometry
	-S: specify disk size
	-r: read partition specs from stdin (implies -i)
	-a: auto-partition with the given style
	-d: dump partition table
	-y: don't ask any questions
	-t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition


Also, does partitioning erase the drive?  I really don't want to lose my data

---

### Post by jken146 on 2008-03-17
Looks like you typed it in wrongly.  Copy and paste (middle click or Ctrl+Shift+V to paste in the terminal) the command if you need to.
```
sudo fdisk -l
```
That's a small L by the way, not the number 1.

---

### Post by egarren on 2008-03-17
It turned out the same, but here is the entire thingy (in Terminal, right?)

Last login: Mon Mar 17 20:06:37 on ttys000
Macintosh-2:~ egarren$ sudo fdisk -l
Password:
fdisk: illegal option -- l
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
	-i: initialize disk with new MBR
	-u: update MBR code, preserve partition table
	-e: edit MBRs on disk interactively
	-f: specify non-standard MBR template
	-chs: specify disk geometry
	-S: specify disk size
	-r: read partition specs from stdin (implies -i)
	-a: auto-partition with the given style
	-d: dump partition table
	-y: don't ask any questions
	-t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition
Macintosh-2:~ egarren$

---

### Post by handydan918 on 2008-03-17
Copy and paste this into your teminal

```
sudo fdisk -l
```
and post the output

---

### Post by egarren on 2008-03-17
I did.  I swear.  I've been copying and pasting this whole time.  Maybe I need to replace fdisk with something else. 

fdisk: illegal option -- l
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
	-i: initialize disk with new MBR
	-u: update MBR code, preserve partition table
	-e: edit MBRs on disk interactively
	-f: specify non-standard MBR template
	-chs: specify disk geometry
	-S: specify disk size
	-r: read partition specs from stdin (implies -i)
	-a: auto-partition with the given style
	-d: dump partition table
	-y: don't ask any questions
	-t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition

---

### Post by jken146 on 2008-03-17
Sorry, you're using a Mac terminal, aren't you?  It seems that fdisk is not the same as in Linux.  From what you posted, it seems that ```
sudo fdisk -d
``` might be the right thing.

---

### Post by egarren on 2008-03-17
Yeah, sorry.  I am using a mac, not linux and I think the output looks better

usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
	-i: initialize disk with new MBR
	-u: update MBR code, preserve partition table
	-e: edit MBRs on disk interactively
	-f: specify non-standard MBR template
	-chs: specify disk geometry
	-S: specify disk size
	-r: read partition specs from stdin (implies -i)
	-a: auto-partition with the given style
	-d: dump partition table
	-y: don't ask any questions
	-t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition

---

### Post by jken146 on 2008-03-17
You might have to boot from a Linux live CD and do ```
sudo fdisk -l
``` from there, unless you have a way of telling us what your partitions are.

---

### Post by egarren on 2008-03-17
Can't I just look in disk utility?  One is 240gb (actually  239,310,209,024 Bytes) and formatted for MOSX, the other is 10gb (10,405,167,104 Bytes) and for MS-DOs (FAT32).  It also says for the windows drive: (see attachment)

---

### Post by jken146 on 2008-03-17
Ok, thanks :)

You should use the "manual" partitioning option in the Ubuntu installer and delete that partition (backup any data on it that you want to keep -- it will be deleted).  Then create a / partition and a swap partition as I described above.

---

### Post by egarren on 2008-03-17
Thanks!  Are you sure that this won't affect my mac partition at all?  Thanks again.

---

### Post by handydan918 on 2008-03-17
> **jken146 said:**
> Sorry, you're using a Mac terminal, aren't you?  It seems that fdisk is not the same as in Linux.  From what you posted, it seems that ```
sudo fdisk -d
``` might be the right thing.

Oh. I didn't get that either. I was somehow under the impression we were running the live cd...

Boy, ya got me. Just tried it on my mac, and even after looking at the man pages, i couldn't get anything you aren't getting...
Maybe it's time for the mac forums.

;-)

---

### Post by jken146 on 2008-03-18
> **egarren said:**
> Thanks!  Are you sure that this won't affect my mac partition at all?  Thanks again.

Not if you do it properly.  Make sure that your mac partition is not going to be formatted before you press the final "next" button in the install wizard.

---

### Post by handydan918 on 2008-03-18
> **jken146 said:**
> Sorry, you're using a Mac terminal, aren't you?  It seems that fdisk is not the same as in Linux.  From what you posted, it seems that ```
sudo fdisk -d
``` might be the right thing.

> **jken146 said:**
> Not if you do it properly.  Make sure that your mac partition is not going to be formatted before you press the final "next" button in the install wizard.

Agreed. That being said, however, all partitioning activities are inherently risky. 
Back it up, man.

---

### Post by egarren on 2008-03-18
> **jken146 said:**
> Ok, thanks :)

You should use the "manual" partitioning option in the Ubuntu installer and delete that partition (backup any data on it that you want to keep -- it will be deleted).  Then create a / partition and a swap partition as I described above.

Sorry to bother you again, but I was wondering why I can't just tell Ubuntu to install on and overwrite the XP partition.  Would it be easier to just not delete it?

---

### Post by handydan918 on 2008-03-18
Ubuntu is going to want a minimum of two - and pereferably three_ partitions. One for root, one for sap, and a separate one for your home directory is good, too. 
This means deleting the existing NTFS partition where Windows now resides. Ubu has too much pride and good sense than to use a NTFS partition, so a new file system will be written as well.

---

### Post by egarren on 2008-03-18
Could someone give me specific instructions on this screen, it seems a little frightening

Attached screenshot

---

### Post by handydan918 on 2008-03-18
> **egarren said:**
> Could someone give me specific instructions on this screen, it seems a little frightening

Attached screenshot


Aye, matey. Here there be monsters...
What do you want to do? 
Are you going to dump the fat32 partition that is highlighted?

---

### Post by egarren on 2008-03-18
> **handydan918 said:**
> Aye, matey. Here there be monsters...
What do you want to do? 
Are you going to dump the fat32 partition that is highlighted?

Yes, I have been told to delete that partition

---

