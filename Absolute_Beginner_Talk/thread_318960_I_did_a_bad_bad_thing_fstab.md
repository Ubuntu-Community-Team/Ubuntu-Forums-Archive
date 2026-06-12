---
title: "I did a bad bad thing fstab"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by thermophile on 2006-12-14
I recently reformatted a partition from ntfs to ext3.  to do that I shifted all of the files from that partition to the other partitions.  so far so good, but then I couldn't get that partition (hda2) to mount.  It would look like it was mounted when I ls -l in the media folder, but I couldn't cd to hda2.  I transfered files using Konqueror to hda2 even though it didn't seem right.  But after I put about 50 gb on the 98 gb partition, I got a message that the drive was full.  That's the point where I started screwing with fstab-thinking that the problem had something to do with the way hda2 was mounting.  heres what that line looks like

/dev/hda2   /media/hda2   ext3   defaults, umask=007, gid=46  0  1

I don't know what I'm doing with this.  I changed part of fstab and rebooted and all my filed disappeared-so I went back into fstab and changed it back which fixed that problem.  but I still have the original somethings not right with the mount.  Konqueror tells me that there are 56 gb on the partition but when I look at GParted it shows that there is only 1.6 gb used.  Also, the partitions where I had temporarially stored the files are still full even though I moved the files back to hda2.  It seems that I copied the files rather than moved them, but I can't see the files in Konqueror or when I ls -l.

help, keep guessing what may be going wrong but I'm afraid that I may do some serious damage.

---

### Post by taurus on 2006-12-14
Try

```
/dev/hda2   /media/hda2   ext3   defaults   0   1
```

---

### Post by thermophile on 2006-12-15
that made all of my files disappear.  Here's what I got when I checked that drive

fredk@fredk-desktop:/media/hda2$ ls -l
total 16
drwx------ 2 root root 16384 2006-12-01 09:52 lost+found

as an aside, do I need to restart my puter every time I change the fstab?

---

### Post by taurus on 2006-12-15
It's best to restart your computer each time you modify your /etc/fstab unless you know what you are doing.  Then, you can unmount the old one an remount it again...

what's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by thermophile on 2006-12-15
I added the umask=007 and can once again see my files.  when I look at the properties in konqueror it says that there are 56gb of files, then down in the free space area it says 1.8mb of 50.7gb.  Also when I look at the disk usage usin GParted (I know that's not it's purpose but I can quickly look at the graphical display and know what's going on)  anyway, gparted shows that 1.6gb out of 98gb is being used.  also there is a little lock beside all the rest of the partitions but not hda2.  that's why I thought it might have something to do with the way the drive was being mounted.

thanks

sudo fdisk -l output:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6068    48741178+   7  HPFS/NTFS
/dev/hda2           12749       25496   102398310   83  Linux
/dev/hda3           25497       30401    39399412+   f  W95 Ext'd (LBA)
/dev/hda4            6069       12748    53657100   83  Linux
/dev/hda5           25497       30138    37286802    b  W95 FAT32
/dev/hda6           30139       30401     2112516   82  Linux swap / Solaris

---

### Post by taurus on 2006-12-15
Are you sure /dev/hda2 is ext3 filesystem, not ext2???

---

### Post by thermophile on 2006-12-15
I'm pretty sure.  I used GParted to reformat it.  it's always possible that I clicked the wrong one but I don't think so.  is there a way to tell for sure?

---

### Post by thermophile on 2006-12-20
ok, so back to my just guessing and changing lines in fstab.  I tried changing hda2 to ext2 just incase that's what I formated.  that didn't change anything, konqueror still says that the 98gb drive is full at 55.6gb.  Also, Gparted still showed the drive as an ext3 even through I had mounted it as ext2.

Any suggestions of where I should go from here?

---

### Post by thermophile on 2006-12-20
the device still isn't mounted according to GParted.  so I tried to mount it

fredk@fredk-desktop:/media$ sudo mount hda2
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

help?

---

