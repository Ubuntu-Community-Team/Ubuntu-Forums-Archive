---
title: "Live CD Ubuntu run not good"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by minhkhoi on 2006-10-13
I am new with Linux. Ubuntu is second Live CD which I run. First is puppy Linux (wonderful everything but hardware driver is very little).

I am strict about hardware driver, Ubuntu is wonderful. My PCMCIA wifi card D-Link run very well. I also heat Linux have very little driver hardware, but I think it don't right now

When run Live CD which download from ubuntu hompage:
1.I can't mout my HDD (FAT and NTFS). 
2.I can't play any media: music (mp3,wma, asf), movie (avi,mpg).
3.I run rarely slow. I hear Linux can run well in slow computer like Pentium 2, but my laptop is Pentium Celeron Mobile 800hz, Ram 256M, HDD 10G, run WinXP perfect.

What should I do?

---

### Post by xyz on 2006-10-13
Is there a problem with the CD itself? Did you check its integrity?
How about md5?

---

### Post by Kateikyoushi on 2006-10-13
> **minhkhoi said:**
> 
When run Live CD which download from ubuntu hompage:
1.I can't mout my HDD (FAT and NTFS). 
2.I can't play any media: music (mp3,wma, asf), movie (avi,mpg).
3.I run rarely slow. I hear Linux can run well in slow computer like Pentium 2, but my laptop is Pentium Celeron Mobile 800hz, Ram 256M, HDD 10G, run WinXP perfect.

What should I do?


1. The same happened to me the live disc did not mount any of my partitions not even reiser or xfs. I guess I could mount by hand but I rather installed it.
2. You can't play media files because the codecs are missing from the live cd after installing Ubuntu you can add the codecs very easily and play media files.
3. Well it runs from an optical disc have to seek, spin up and down,it  runs much faster once installed.

---

### Post by pay on 2006-10-13
The media formats you described are properitery formats and for Ubuntu to include thme would be illegal (I think, well at the very least they aren't opensource and Ubuntu doesn't include non-opensource software).
To mount drives you need to edit the fstab.
```
sudo mkdir /media/drive
sudo nano /etc/fstab
```
then add ```
/dev/hda1    /media/drive ntfs  nls=utf8,umask=0222 0    0
``` at the end for ntfs or```
/dev/hda1    /media/drive vfat  iocharset=utf8,umask=000  0    0
```for fat assuming your partition is hda1
remount fstab```
sudo mount -a
```
I'm not entirely sure if you can do this with the liveCD however.

---

### Post by Kateikyoushi on 2006-10-13
It is easier just to mount them manually all settings are lost anyway.

Make a mount folder.

```
sudo mkdir /media/windows
```

Then mount them

For NTFS
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

For FAT
```
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```
Replace hda1 with your hard drives and repeat if necessary.

---

### Post by minhkhoi on 2006-10-13
Thanks everybody. I'll install Ubuntu in HDD

---

