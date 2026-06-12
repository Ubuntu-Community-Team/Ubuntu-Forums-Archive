---
title: "DVD/DVD-R/DVD-RW won't read or burn."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Daghita on 2007-12-28
Most of the problems I've run into with Ubuntu I've been able to get figured out. But, this one I'm having a bit of trouble. I've combed through the forums a bit and haven't found any solutions.

1) I am using a Pioneer DVD-RW DVR-K12D
2) I can play or burn CDR media just fine.
3) I can't play or burn DVD, DVD-R, or DVD-RW media.
4) The OS will mount the DVD, DVD-R, or DVD-RW as blank media.
5) I've installed tons of codecs to make sure those bases were covered.

If it helps:
```

tad@tad-laptop:~$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 4 2007-12-27 10:26 /dev/dvd -> scd0
tad@tad-laptop:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 4 2007-12-27 10:26 /dev/cdrom -> scd0

```

From VLC:
```

tad@tad-laptop:~$ vlc /media/cdrom0
VLC media player 0.8.6c Janus
/home/tad/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/tad/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000281] main playlist: playlist is empty

```

The FSTAB
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa8af6b0-3cee-456f-9fec-3246dbc7c7a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d0326a70-4e21-494c-871a-7ff9e620e9a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```


At the moment, I'm not really sure where to start to fix this problem...

---

### Post by CCNA_student on 2007-12-28
What program are you using to burn DVD's?

---

### Post by Daghita on 2007-12-28
I'm currently using K3b

---

### Post by Daghita on 2007-12-28
...bump.

---

### Post by mc4man on 2007-12-28
i believe that drive had some reliability issues even when new, it's probably on its way out. You could try a lens cleaning disk, may get some extra miles off of it. As a side note I wouldn't doubt it might still work under windows

---

### Post by Daghita on 2007-12-28
I have an old version of PHLAK that is a livecd that you can boot from on a DVD-RW. I put it in the drive and restart the computer and it started booting off the disk just fine. So, if anything, the drive should be able to read a DVD-R.

---

### Post by mc4man on 2007-12-29
That's why i think the drive will probably still be operational in windows, there's something (just my conclusion from a similar experience) in ubuntu/linux, hal, whatever, that is "unfriendly' to older, marginal drives. When your booting from a disc your not in the Os.,kernel, hal, ect.

---

### Post by Daghita on 2007-12-30
It would appear that after a LOT of reading that this situation is somewhat common. I'll hold out, I know someone in the Linux world will get it figured out.

---

### Post by mp035 on 2008-01-04
Hello all,
I have the exact same problem, on gutsy, and my dvd-burner is only 2 months old.

anyone found anything on it yet?

---

### Post by onus on 2008-02-11
yeah i cant make dvds!  whats the solution?!?!  

using avs and devede and w/e else it makes no matter.  

AVS: says "no cd/dvd drives found."

whereas w/ devede i can create the iso's and burn them to disks but the disks only work on my comp. and it specifically says: "a classic video dvd, playable in all dvd players."

help....

---

