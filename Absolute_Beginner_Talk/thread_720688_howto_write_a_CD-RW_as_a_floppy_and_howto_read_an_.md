---
title: "howto write a CD-RW as a floppy and howto read an Adaptec-created UDF CD-RW"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mvdberg112 on 2008-03-10
I'm a bit new to Linux on some points, escpecially when it comes to 'newer' technology.

I've DVD-RW player from LG, which works just fine, i.e. mounting and reading from CDs works.
I have one CD-RW which has been written using DirectCD 5.3.4.21 on a W2k Sp4 system. On W2k I can read all files dragged and dropped on the CD (about 500 MB).
When inserted in the Linux system it shows to files in the root and no directories: autorun.inf  udfrinst.exe.
Why? Where are the other files? How can I read these UDF files.

I've tried to following lines in the /etc/fstab:
```
# 2008-03-10 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 rw,users,noauto,exec 0       0
#/dev/scd0       /media/cdrom0    iso9660 noauto,ro,user,users,gid=users   0 0
#/dev/scd0       /media/cdrom0    udf noauto,noatime,rw,user,gid=users 0 0
#/dev/scd0       /media/cdrom0       udf             sync,noauto,noatime,rw,users    0 0
/dev/scd0       /media/cdrom0   udf,iso9660 rw,users,noatime,noauto,exec,gid=users 0       0
```
The lines with only 'udf'  as type did not work. Also this did not work:
```
root@emea-l3-mberg02:/usr/src/linux-headers-2.6.22-14# mount -t udf -o rw,users,noatime,noauto,exec,gid=users /dev/scd0 /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@emea-l3-mberg02:/usr/src/linux-headers-2.6.22-14# mount -t udf /dev/scd0 /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
What am I doing wrong?
System info:```
Linux hostname 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
```

---

### Post by philinux on 2008-03-10
Try this in fstab

/dev/scd0 /media/cdrom0 iso9660,udf user,noauto 0 0

---

### Post by mvdberg112 on 2008-03-11
You wrote:> **philinux said:**
> Try this in fstab
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto 0 0
I did try this, same result: the files that are on the CD, I cannot see and I see only two other files. It seems that the CD has "two levels" or two tracks, and that I am looking at the first one, but that the other files are in the second one. Thanks for your help anyway; it looked most logical to me!

Any help that makes the other files readable? Thanks in advance!

```
root@hostname:/usr/src/linux-headers-2.6.22-14# cat /etc/fstab | tail -n 1
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto 0 0
root@hostname:/usr/src/linux-headers-2.6.22-14# umount /dev/scd0
root@hostname:/usr/src/linux-headers-2.6.22-14# mount /dev/scd0
root@hostname:/usr/src/linux-headers-2.6.22-14# ls -l /media/cdrom0
total 413
-r-xr-xr-x 1 root root     65 2005-08-08 08:54 autorun.inf
-r-xr-xr-x 1 root root 421524 2005-08-08 08:55 udfrinst.exe
root@hostname:/usr/src/linux-headers-2.6.22-14# 
```

Any help that makes the other files readable?

---

### Post by philinux on 2008-03-11
Just double checking.

I assume you did reboot following the changes to fstab.

---

### Post by mvdberg112 on 2008-03-11
Actually, I did not reboot. 
I was always thinking as follows, let me know if I am wrong, because I can only learn of it:
Reason: attempting a mount using the device or mount point only (for eample  "mount /dev/scd0"  or "mount /media/cdrom0"), should read the corresponding line in the /etc/fstab and make so the change active; as far as I know does Linux not 'remember'  and use the settings in the fstab other then with a mount: every time a mount is done, the file is read.
The other reason was, that all the options were specified on the command line, bypassing the fstab. I have always done it this way and assumed that was a valid procedure, although the change of fstab makes the changes permanent over a reboot.
Thanks for the suggestion, because it helps to get things clear.

---

### Post by mvdberg112 on 2008-03-11
Bad Luck, Good Luck. In the mean time I continued to try. I  found this:
[http://ubuntuforums.org/showthread.php?t=490087&highlight=cdrom+udf](http://ubuntuforums.org/showthread.php?t=490087&highlight=cdrom+udf)
[http://sidux.com/PNphpBB2-viewtopic-t-2477.html](http://sidux.com/PNphpBB2-viewtopic-t-2477.html)

I tried a few commands, but no avail. Then reformatted to CD by accident using cdrwtool, (cdrwtool -d /dev/scd0 -w mode2 -l 3 -m 295232). Since the CD was now not at all readable anymore, the following format was done:
> root@emea-l3-mberg02:/home/michael# cdrwtool -d /dev/scd0 -q
                       Which gave an error: 
Formatting track
wait_cmd: Input/output error
Command failed: 04 17 00 00 00 00 00 00 00 00 00 00 - sense 00.00.02
format disc: Illegal seek
Then reformatted the CD with DirectCD and tried again the mount:
> # mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdrom0
mount: /dev/pktcdvd/0: can't read superbl
Then I read the second thread
[http://sidux.com/PNphpBB2-viewtopic-t-2477.html](http://sidux.com/PNphpBB2-viewtopic-t-2477.html)
And here it said that it sometimes works without using /dev/pktcdvd/0, so then this:
[quote]# mount -t udf -o rw,noatime,async /dev/scd0 /media/cdrom0[\quote]
And this worked! WHY? I have no idea! I tried this before. Even if the option are left out the command works (i.e. # mount -t udf /dev/scd0 /media/cdrom0).
I can only explain it that the CD-RW format contained an error.
After this I one file with Linux was copied on to the CD and that worked. Then an umount followed by a mount and it did not work anymore. Put the CD in the WinXP and it mounted only the ISO part. DirectCD found errors: it was only able to recover one file... Conclusion: some incompatiblity between DirectCD v5.3.4.21 (and  v5.3.4.2 too, because that was the format of the fist CD-RW) and Linux 2.6.22-14-generic and/or udftools 1.0.0b3-12 exists. Who know shoudl tell us.

Second problem that remains is this: in what cases do we need udftools (which every website seems to tell about) and in which case not?

---

