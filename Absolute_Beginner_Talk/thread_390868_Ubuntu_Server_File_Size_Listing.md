---
title: "Ubuntu Server File Size Listing?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by gh0stb0y on 2007-03-22
Hi All,  noob question here, but I recently setup a Ubuntu file server using the server edition of Ubuntu and have been perplexed as to why my 120GB HD is telling me that it's out of space after 12GB of use.  It was re-partioned as ext3 so it should've been empty.  Been trying to find a command similar to chkdsk in Windows environments or even DIR /s/a that lists the file sizes of all files/directories on the drive.  Whenever I use df -h, it only lists /dev/hda1 not the other two HDs that I've got mounted as separate folders.  Is there a way to check?  Thanx.

---

### Post by Bachstelze on 2007-03-22
If *df* doesn't list your drives, it means they are not mounted, that might very well be your problem.

---

### Post by gh0stb0y on 2007-03-22
eh?  but i can copy to those directories...how would they not be mounted?  my /etc/fstab looks like this:

/dev/hdb1 /mnt/400gb default 0 0
/dev/hdc1 /mnt/120gb default 0 0

and my df -h looks like this:
root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             187G  175G  2.0G  99% /
varrun                126M  140K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M   92K   10M   1% /proc/bus/usb
udev                   10M   92K   10M   1% /dev
devshm                126M     0  126M   0% /dev/shm

---

### Post by Bachstelze on 2007-03-22
That means nothing. Even if there is nothing mounted in the dir, you can put stuff into it, maybe that's why your root partition is already full...

---

### Post by gh0stb0y on 2007-03-22
Oh, now that you mentioned it, it does appear that all the stuff I've been dumping to the server is around that file size.  Then how to I properly mount the drives?  Now that I look at it more carefully, i've got default and not defaultS.  Would this have made the error in the mount?  Does this mean that I've gotta empty out those directories first before I can mount?  Doh!

---

### Post by Bachstelze on 2007-03-22
You also forgot the filesystem. For info, here's my fstab :

```
proc            /proc           proc            defaults        0       0
/dev/hda8       /               reiserfs        defaults        0       1
/dev/hda9       /tmp            reiserfs        defaults        0       2
/dev/hda10      /usr            reiserfs        defaults        0       2
/dev/hda11      /var            reiserfs        defaults        0       2
/dev/hda1       /boot           ext3            defaults        0       2
/dev/hda5       none            swap            sw              0       0
/dev/hda7       /debian         reiserfs        defaults        0       2
/dev/hda6       /debian/home    ext3            defaults        0       2
/dev/hda12      /freebsd        ufs             ro,ufstype=ufs2 0       0
/dev/hda13      /freebsd/tmp    ufs             ro,ufstype=ufs2 0       0
/dev/hda16      /freebsd/usr    ufs             ro,ufstype=ufs2 0       0
/dev/hda14      /freebsd/var    ufs             ro,ufstype=ufs2 0       0
/dev/hdb        /media/cdrom    udf,iso9660     user,noauto     0       0
shm             /dev/shm        tmpfs           nodev,nosuid,noexec     0 0

```

---

### Post by gh0stb0y on 2007-03-22
Yikes....thanx, I'll be moving the files before I reboot with the new mount!

---

