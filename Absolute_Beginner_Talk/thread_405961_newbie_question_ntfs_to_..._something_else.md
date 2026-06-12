---
title: "newbie question: ntfs to ... something else"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by svjenni on 2007-04-10
Another newbie question i'm afraid

I have finally managed to get my creative zen talking to my pc but all my music is on a ntfs drive.  This is not a problem right now, but I am taking the bull by the horns

so I have put all my files onto my Ubuntu partition to back them up

Am I right in thinking I can just use the command...  sudo mke2fs -j /dev/hdb1??

I have looked for some info about ext3 but can't find much...Is there anything I should know before I do this?  is ext3 the standard for linux?

---

### Post by Maestro23 on 2007-04-10
You can use nfts-3g to enable read/write access on the ntfs partiton.

NTFS-3G: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

*It is available in the repositories.

---

### Post by svjenni on 2007-04-10
yeah but i wanna be microsoft free if possible!

---

### Post by taurus on 2007-04-10
> **svjenni said:**
> 

Am I right in thinking I can just use the command...  sudo mke2fs -j /dev/hdb1??

I have looked for some info about ext3 but can't find much...Is there anything I should know before I do this?  is ext3 the standard for linux?

Yes, but you need to umount /dev/hdb1 first if you want to convert it from ntfs to ext3.  Again, make sure it is /dev/hdb1.

```
sudo umount /dev/hdb1
sudo mke2fs -j /dev/hdb1
```
Now, you need to either modify the entry in /etc/fstab for /dev/hdb1 or add it in there so it would be mounted automatically each time you boot.

---

### Post by svjenni on 2007-04-10
thanks, nearly there

I'm trying to re mount the drive but i get the error

jenni@home:~$ sudo gedit /etc/fstab
jenni@home:~$ sudo mount -a
[mntent]: line 9 in /etc/fstab is bad


here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ed9cd317-f23f-41b5-8407-92f01b014438 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1172076c-a6cd-4c59-9854-9cb0b6fe69c4 none            swap    sw              0       0
/dev/hdb1	/media/music and video	ext3   rw,user          0             2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


what am i doing wrong?

---

### Post by taurus on 2007-04-10
> **svjenni said:**
> thanks, nearly there

I'm trying to re mount the drive but i get the error

jenni@home:~$ sudo gedit /etc/fstab
jenni@home:~$ sudo mount -a
[mntent]: line 9 in /etc/fstab is bad


here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ed9cd317-f23f-41b5-8407-92f01b014438 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1172076c-a6cd-4c59-9854-9cb0b6fe69c4 none            swap    sw              0       0
**/dev/hdb1	/media/music and video	ext3   rw,user          0             2**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


what am i doing wrong?

There shouldn't be a space in "**/media/music and video**".  So, either try '/media/music and video' or /media/music_and_video.  And if course, you need to create that new mount point if you want to use the second option.

```
sudo mkdir /media/music_and_video
```

p.s.  And please try to use gksudo if you want to use gedit.

```
gksudo gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by svjenni on 2007-04-10
got it, mounted it to music instead

---

