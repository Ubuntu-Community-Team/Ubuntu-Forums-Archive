---
title: "[SOLVED] external hard drive not showing up"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by peterjohn on 2007-11-14
Hi, I have a 500 gig seagate hard drive I hooked it up and It is not showing up in the my computer folder, it's in my device manger but it doesn't really recognize it, umm I'm also running it off the live cd, but I thought that that wasn't supposed to matter because thats what the live cd's here to do, check hardware, right?.  Well sum supporte would be nice 
Thank you guys,
-peter

---

### Post by peterjohn on 2007-11-14
bump? anyone

---

### Post by taurus on 2007-11-14
You can still mount it by hand if you want to access it.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by peterjohn on 2007-11-14
Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa896150f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7669b61e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 





I get that the first one is the internal and the second one is the external but what do I do with this?

---

### Post by taurus on 2007-11-14
```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
ls -la /media/sda1
```

---

### Post by Harpoon on 2007-11-14
Hmmm.  You say that the drive is "hooked up."  Am I correct in assuming that you mean via  USB?  The output you posted indicates that the system does not see the drive at all.
check that the drive cables are all plugged in correctly;
check that the drive is powered up (spinning);

if this is a new drive, did you partition it the way you want it and/or did you format it yet?  If the drive is not formatted, linux should still "see" it, but you won't be able to "use" it.

If the drive is connected via USB and all other things seem correct, then check the drive jumper and make sure it is set to "Master" (no slave present).  I have a couple of USB interfaces that absolutely require this.  If it is set wrong, I have the problem you describe.

BTW, the output you posted shows  "sda.."  This is your first drive.  The next one should show as "sdb"

---

### Post by Duck2006 on 2007-11-14
I may be wrong but is this the second drive?

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7669b61e

Device Boot Start End Blocks Id System
/dev/sda1 * 1 60801 488384001 c W95 FAT32 (LBA)

---

### Post by Harpoon on 2007-11-14
Sorry, I misread the output.  (Still working on the first cup of coffee).

The drive is seen and is formatted.  All is well.

Please check the jumper settings and try to mount the drive manually.

Apologies.

---

### Post by peterjohn on 2007-11-16
> **taurus said:**
> ```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
ls -la /media/sda1
```

ok I did this and this is the output

total 269632
drwxrwxrwx  9 root root    32768 1970-01-01 00:00 .
drwxr-xr-x  5 root root      100 2007-11-16 16:14 ..
drwxrwxrwx 63 root root    32768 2006-11-22 09:43 anime
-rwxrwxrwx  1 root root 79752708 2007-05-10 22:06 Banned Cartoons - Betty Boop - Popeye The Sailor (With Betty Boop).mpg
-rwxrwxrwx  1 root root 65360176 2007-05-11 17:34 Banned Cartoons - Nazi - Popeye - Spinach Fer Britain (WW2).mpg
-rwxrwxrwx  1 root root 70109100 2007-05-10 21:47 Bugs Bunny Foghorn Leghorn - Little Boy Boo.mpg
drwxrwxrwx 14 root root    32768 2007-05-14 00:08 Death Note
drwxrwxrwx  2 root root    32768 2007-05-14 01:51 New Folder
drwxrwxrwx  8 root root    32768 2007-01-08 01:13 OSTAnime
drwxrwxrwx  2 root root    32768 2006-11-21 15:10 Recycled
drwxrwxrwx  3 root root    32768 2006-11-21 15:00 System Volume Information
-rwxrwxrwx  1 root root   132608 2007-08-30 18:43 Thumbs.db
-rwxrwxrwx  1 root root 50407428 2007-05-11 17:32 Tom & Jerry - Little School Mouse.mpg
-rwxrwxrwx  1 root root   266544 2007-08-19 13:51 unicows.exe
-rwxrwxrwx  1 root root  9679815 2007-08-08 18:28 vlc-0.8.6c-win32.exe
drwxrwxrwx 11 root root    32768 2006-11-22 00:32 wot


 and I still can't find the drive anywhere?? please help!:confused::(

-peter

---

### Post by Inxsible on 2007-11-16
> **peterjohn said:**
> ok I did this and this is the output

total 269632
drwxrwxrwx  9 root root    32768 1970-01-01 00:00 .
drwxr-xr-x  5 root root      100 2007-11-16 16:14 ..
drwxrwxrwx 63 root root    32768 2006-11-22 09:43 anime
-rwxrwxrwx  1 root root 79752708 2007-05-10 22:06 Banned Cartoons - Betty Boop - Popeye The Sailor (With Betty Boop).mpg
-rwxrwxrwx  1 root root 65360176 2007-05-11 17:34 Banned Cartoons - Nazi - Popeye - Spinach Fer Britain (WW2).mpg
-rwxrwxrwx  1 root root 70109100 2007-05-10 21:47 Bugs Bunny Foghorn Leghorn - Little Boy Boo.mpg
drwxrwxrwx 14 root root    32768 2007-05-14 00:08 Death Note
drwxrwxrwx  2 root root    32768 2007-05-14 01:51 New Folder
drwxrwxrwx  8 root root    32768 2007-01-08 01:13 OSTAnime
drwxrwxrwx  2 root root    32768 2006-11-21 15:10 Recycled
drwxrwxrwx  3 root root    32768 2006-11-21 15:00 System Volume Information
-rwxrwxrwx  1 root root   132608 2007-08-30 18:43 Thumbs.db
-rwxrwxrwx  1 root root 50407428 2007-05-11 17:32 Tom & Jerry - Little School Mouse.mpg
-rwxrwxrwx  1 root root   266544 2007-08-19 13:51 unicows.exe
-rwxrwxrwx  1 root root  9679815 2007-08-08 18:28 vlc-0.8.6c-win32.exe
drwxrwxrwx 11 root root    32768 2006-11-22 00:32 wot


 and I still can't find the drive anywhere?? please help!:confused::(

-peterThe fact that it lists all the files in your external drive means that ubuntu can see it and access it.

if you want to "explore" it (like windows explorer) open up nautilus and navigate to /media/sda1

Or go to Places>>sda1

---

### Post by peterjohn on 2007-11-16
wow I was really stupid.  [I] thought that the drive would show up on the desktop or in places>computer thanks everyone for putting up with me 

-peter

---

