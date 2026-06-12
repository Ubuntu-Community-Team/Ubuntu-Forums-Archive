---
title: "How to browse an NTFS disk"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by LadyLuck on 2006-06-11
HI all. I have dapper drake on an old Dell box with two hard drives dev/hda1 and dev/hdb1.  The second hard drive (NTFS) contains old files that I am reluctant to throw away without checking them first. 

The following lines are from /etc/fstab:
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,umask=0222 0   0

In the GUI tool "Disks Manager" both hard drives show up but attempting to browse hadb1 results in failiure. In addition turning Firefow to /media/ to look for hdb1 does not work (it correctlly lists two CDROM and incorrectly two Floppy drives (only one present))

I should add that the NFTS drive still contains an old version of XP but I cannot boot from this disk.

Any tricks I can use to browse the content of the hdb1 drive?

thank you, LL

---

### Post by Kilz on 2006-06-11
[QUOTE=LadyLuck]HI all. I have dapper drake on an old Dell box with two hard drives dev/hda1 and dev/hdb1.  The second hard drive (NTFS) contains old files that I am reluctant to throw away without checking them first. 

The following lines are from /etc/fstab:
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,umask=0222 0   0

In the GUI tool "Disks Manager" both hard drives show up but attempting to browse hadb1 results in failiure. In addition turning Firefow to /media/ to look for hdb1 does not work (it correctlly lists two CDROM and incorrectly two Floppy drives (only one present))

I should add that the NFTS drive still contains an old version of XP but I cannot boot from this disk.

Any tricks I can use to browse the content of the hdb1 drive?

thank you, LL[/QUOTE]

Have you tried creating the /media/hdb1 directory and rebooting?
sudo mkdir /media/hdb1

---

### Post by LadyLuck on 2006-06-11
[QUOTE=Kilz]Have you tried creating the /media/hdb1 directory and rebooting?
sudo mkdir /media/hdb1[/QUOTE]

Ok thanks that helped. I errouneously assumed that the all enties in "fstab" are always mounted and that since /media/hdb1 is listed by the "Disks Manager" the directory /media/hdb1 must exist (but hey Im learning)

Now trying something like

$ sudo mount -r -s -t ntfs hdb1 /media/hdb1 -o utf8
returns
mount: special device hdb1 does not exist

what am I missing?

---

### Post by richbarna on 2006-06-11
Follow this guide, and you'll be sorted in minutes ;)
[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

---

### Post by LadyLuck on 2006-06-11
> **richbarna]Follow this guide, and you'll be sorted in minutes  said:**
> http://www.psychocats.net/ubuntu/mountwindows.php[/URL]

Thanks for pointing out that excellent resource but I'm still in some trouble

After rebooting my fstab contains this line
**/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222 0   0**
but running 
sudo mount -a
gives the following error: 
[B]mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error[/B]

Runnig sudo fdisk -l returns
 [B]  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1322     9994288+   7  HPFS/NTFS[/B]

Any further assistance appreciated.

---

### Post by LadyLuck on 2006-06-12
Sorry for being puushy but this is the error from dmesg | tail
[SIZE="2"]
[4295639.637000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4295639.637000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4295639.638000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS vol ume.[/SIZE]

Am I correct in thinking the boot sector is corrupt, hence I cannot boot from it and therefore the drive does not mount properly? If so can I skip the boot sector and mount the rest?

---

### Post by LadyLuck on 2006-06-13
Well things are getting funnier all the time (funny strange not funny ha ha). I booted to a live cd and ran QTparted to find that my hdb1 volume was listed as a linux volume ext3. I went back to Ubuntu botting from the hard drive (hda1) and fiddeled with fstab:
commented out
*#/dev/hdb1      /media/hdb1     ntfs    nls=utf8,umask=0222     0       0*
and added
*/dev/hdb1      /media/hdb1      ext3    defaults        0       2*

I then ran 
**sudo mount -a **
and hdb1 mounted without problems. However I was unable to save anything to it although as far as I can see permissions are set correctly.

Now attempting 
**sudo fdisk -l**
returns (as before)

[SIZE="2"][B]Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
etc. etc.

Disk /dev/hdb: 10.2 GB, 10242892800 bytes
240 heads, 63 sectors/track, 1323 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1322     9994288+   7  HPFS/NTFS
[/B][/SIZE]

(note the last line). Is it possible that this drive has an old boot sector with and old LILO or GRUB? (the disk originally comes from a late nineties dual boot Red Hat/Windows Compaq machine). QTparted listed a 600 MB partition but had little infor on it (NTFS ext3 or otherwise).
I'm assuming the disk is caputt and I am planning a removal and funeral for saturday june 17th at 14:00 GMT. :-({|= 
Thanks to those who tried to help.

---

### Post by bodycoach2 on 2006-06-13
I went into Synaptic, and did a search for anything ntfs. I loaded anything I could, and it worked. I'm able to use my ntfs drive. Not sure why, or how, but all I care is that it works. Redneck Ubuntu programming, maybe?

---

