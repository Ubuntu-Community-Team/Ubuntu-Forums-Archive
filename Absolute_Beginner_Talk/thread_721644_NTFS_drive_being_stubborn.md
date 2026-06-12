---
title: "NTFS drive being stubborn"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Alarindris on 2008-03-11
Been having a heck of a time trying to get my NTFS drive mounted.


sudo ntfsfix /dev/sda1
```

returns

Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed : No such file or directory
```

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

returns (and this is the problem)

```
Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, so mounting could be done safely.
```

fstab shows


```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=2e87ebfa-7c7d-4224-8315-089956dd5e7b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=8C84D1A984D19654 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=8444ABB144ABA500 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=613ba121-cd5f-4a4a-ba26-9320495e5918 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sda1 	/media/windows  ntfs-fuse auto,gid=1001,umask=0002 0 0
```

You can see in fstab I tried fuse, but no luck.

What is "properly shutting down windows?" I've gone back in, shut down, restarted, logged off and then shut down... tried all that. Hibernation has always been disabled on my PC and I've never knowingly used it. I've gone so far as to disabling the drive in windows, didn't help either. Note that it functions properly in XP.

Also, when I look in /dev sda1 is 34.5 MB when it's actually a 500GB drive, no other partitions.

Help meh!

Thanks in advance to any responses.

---

### Post by forrestcupp on 2008-03-11
So you actually started Windows up and Shut it down, and it went through the complete shutdown process until the computer was off?  You didn't have to press the power button to shut it off?

If it really did shut down properly, you could try booting to Windows and defragmenting your hard drive, then run chkdsk on it.  [Here](http://www.updatexp.com/windows-xp-chkdsk.html) is a guide on how to run chkdsk in XP.

---

### Post by Oldsoldier2003 on 2008-03-11
> **forrestcupp said:**
> So you actually started Windows up and Shut it down, and it went through the complete shutdown process until the computer was off?  You didn't have to press the power button to shut it off?

If it really did shut down properly, you could try booting to Windows and defragmenting your hard drive, then run chkdsk on it.  [Here](http://www.updatexp.com/windows-xp-chkdsk.html) is a guide on how to run chkdsk in XP.

Yes I would boot windows, chkdisk/defrag then cleanly shut down windows. If that doesn't fix the problem then its time to dig deeper into the issue.

---

### Post by Alarindris on 2008-03-11
Yep, shutdown works properly, I waited until the computer was actually off (didn't have to hit the button.)  After I ran ntfsfix, I booted into windows and it checked the disk automatically, said it was just fine.  Is defragging really nessecery?   I haven't used the drive at all really, only got it about 6 months ago.  But I will try if you think it'll make a difference.

---

### Post by Alarindris on 2008-03-11
Wow. My drive is 25% fragmented.  Gonna defrag for the next 10 hours and see what happens : /

---

### Post by Alarindris on 2008-03-11
Decided not to defrag all night, so I backed up the necessities, wiped the drive clean and all is AOK.

---

