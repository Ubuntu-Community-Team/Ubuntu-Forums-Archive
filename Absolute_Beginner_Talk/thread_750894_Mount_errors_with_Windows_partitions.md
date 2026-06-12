---
title: "Mount errors with Windows partitions"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by David1000 on 2008-04-10
I have installed Ubuntu 7.10.  I have two hard discs with 5 Windows partitions on both.

After installation, I can see only 7 of the 10 Windows partitions.

I have checked Gparted and FStab.

The mount point for hda1 is given as /media/hda1, /media/hdb1.   hdb1 can not be seen.

hdb8 is not mounted and can not be seen.

hda5 is mounted but can't be seen.

I can see no problems with the fstab file.

The ftab file is as below.   Any ideas as to the cause of the problem and solution?



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda13
UUID=b1e07d87-c873-4ff4-8f1e-e736e36740e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda9
UUID=0cd9414e-8d43-4dcd-b3b8-9489941ed593 /boot           ext3    defaults        0       2
# /dev/hda12
UUID=973152a8-ede0-4672-b9e4-adde47e39b6c /home           ext3    defaults        0       2
# /dev/hda1
UUID=231D-16DA  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=1561-180E  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=1768-1CD8  /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda8
UUID=334E-29B0  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=231D-16DA  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=1FF9-6224  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=D5C0-9BA2  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=2833-410D  /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb8
UUID=334E-29B0  /media/hdb8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda11
UUID=8bb0db2f-1a6b-4ed9-ade6-2537c1b7fed1 /usr            ext3    defaults        0       2
# /dev/hda10
UUID=67b0c2db-3614-4c1e-bfc1-4dfae27da5bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by eternicode on 2008-04-10
What do you mean by "can't be seen"?  If you're talking about in GParted, that's strange.  What's the output of "sudo fdisk -l" ?  This should tell you what drives have what/how many partitions.

What makes you think hda5 is mounted?  (run "mount" at a command line to see what's mounted where)

Just to quickly check that your UUIDs are correct, post the output of
```
sudo blkid /dev/dhb1 /dev/hdb8 /dev/hda5
```
The UUIDs given for these devices should match what's in your fstab.  I'd be surprised if they didn't, given it's a fresh install, but you never know.

---

### Post by David1000 on 2008-04-10
Made some progress.  Thanks for the help.

When I said that the partition could not be seen, I meant that if could not be seen in File Browser (Nautilus).

In Fstab, the UUIDs were missing for hda5.  I put them in and now hda5 shows in file browser but not the contents.  I tried manually mounting the partition as it was unmounted (according to Mount) but still no joy.

hda1 and hdb1 have the same UUIDs in fstab.  ditto hda8 and hdb8.  This no-doubt explains the double mount point shown in Gparted.

I noticed at last reboot, that there were error messages but it was all too fast and meaningless for me to make sense of.

Would it be best it I reinstall?  Would I need to wipe the linux folders first to prevent faulty settings carrying over?

---

### Post by eternicode on 2008-04-11
If you're willing to reinstall, it couldn't hurt.  You don't need to wipe the folders, just be sure to check the "format" checkbox when choosing where to mount your root and /boot directories.  You could also format /home, if you wanted, but it's not necessary.

Also, if you see those boot-time error messages again, try to see what they say.

---

### Post by vanadium on 2008-04-11
To see why some partitions won't mount, you might want to run the command

sudo mount -a

This "remounts" all drives according to fstab. This command will produce output only when there are errors. Post that output here and we can then help troubleshooting, one partition at the time if the need arises.

Of course, you could reinstall, but that certainly should not be necessary.

---

### Post by David1000 on 2008-04-13
Been away for the weekend, hence the break in this thread.

Sudo mount -a gives:
david@AMD5200:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/0000-0D73 does not exist

so I guess that is why hda5 won't mount.  But why the error?  UUID correct according to Blkid.  And how come hda1 and hdb1 have the same UUID.  Ditto hda8 and hdb8.  Is there a way I can find the correct UUID's so I can manually fix?

david@AMD5200:~$ sudo blkid
/dev/hda1: LABEL="BU-BOOT" UUID="231D-16DA" TYPE="vfat" 
/dev/hda5: LABEL="WDC DATA" UUID="0000-0D73" TYPE="vfat" 
/dev/hda6: LABEL="HENLEY" UUID="1561-180E" TYPE="vfat" 
/dev/hda7: LABEL="WDC PHOTOS" UUID="1768-1CD8" TYPE="vfat" 
/dev/hda8: LABEL="TOPO" UUID="334E-29B0" TYPE="vfat" 
/dev/hda9: UUID="0cd9414e-8d43-4dcd-b3b8-9489941ed593" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda10: TYPE="swap" UUID="67b0c2db-3614-4c1e-bfc1-4dfae27da5bb" 
/dev/hda11: UUID="8bb0db2f-1a6b-4ed9-ade6-2537c1b7fed1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda12: UUID="973152a8-ede0-4672-b9e4-adde47e39b6c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda13: UUID="b1e07d87-c873-4ff4-8f1e-e736e36740e7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb1: LABEL="PROGRAMMES" UUID="231D-16DA" TYPE="vfat" 
/dev/hdb5: LABEL="BU-GENERAL" UUID="1FF9-6224" TYPE="vfat" 
/dev/hdb6: LABEL="BU-PHOTOS" UUID="D5C0-9BA2" TYPE="vfat" 
/dev/hdb7: LABEL="ACRONIS" UUID="2833-410D" TYPE="vfat" 
/dev/hdb8: LABEL="ORIG-PHOTO" UUID="334E-29B0" TYPE="vfat"

---

### Post by vanadium on 2008-04-14
It is a strange situation you have indeed. I am not sure about the error message of mount -a. It refers to uuid 0000-0D73 which is unique to /dev/hda5, yet in fstab, that uuid is never referred to: the drive is mounted directly by device name.

UUID's are what they are for the drive. They can indeed be identical, although for regular ext2 linux volumes and the way the UUID is generated for these, chances to have two identical ones is 0.0000%. Probably it is quite different for fat volumes. This means that in this case, you can't use the UUIDS as unique identifier.

I see that all you volumes have neat, unique labels. What I advise you, therefore, is to mount all your vfat volumes using their LABEL instead of their UUID instead. Make a backup copy of your current tab, then change all lines referring to vfat volumes to use the label instead of the uuid. For example:

# /dev/hda1
UUID=231D-16DA /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1

becomes

LABEL="BU-BOOT" /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 2

(notice that I also changed the last number to 2. Only your system drive should have first priorit y in checking).

Do this for all your vfat volumes. When your /etc/fstab is updated, run "sudo mount -a" and again take note of any error messages.

---

### Post by David1000 on 2008-04-17
Thanks for all your help.  In the end, I deleted problem partitions and then converted then to ext3.  Problem solved; for now.

---

