---
title: "Burning an ISO"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by hamishnz on 2007-09-29
Hi All,

I have just downloaded a ISO file and need to write it to a DVD.
Can I just use the "Places>CD/DVD Creator" Progam ?

Thanks Hamish

---

### Post by FuturePilot on 2007-09-29
Yep, that will work. When you click Burn it will ask you if you want to burn it as a file or as an image. Select the Burn from Image option.
There are also other apps in the repos for burning. Such as Gnomebaker or K3B. But the default one will get the job done for you.:)

---

### Post by hamishnz on 2007-09-29
Ohh thanks for much for that:)
Would anyone be able to explain to me what a ISO file is ?

Thanks Again Hamish

---

### Post by SpiritIsReality on 2007-09-29
howdy
many people contribute to wikipedia, and I'll let them explain it
[http://en.wikipedia.org/wiki/Iso9660](http://en.wikipedia.org/wiki/Iso9660)
they can put it into words so much better than I can, seeing as I barely know it's
a file that goes on a cd  that boots when you put it in the cdrom

trails

---

### Post by alienexplorers on 2007-09-29
No matter what program you use to burn the .iso image, make sure you do it at the slowest speed your burner will burn.  Also before burning check the MD5 checksum of the .iso file using:
> md5sum Ubuntu_version.iso
After you burn the image CD, boot it and use the check disk for errors option to make sure your disk burnt correctly.  After all that you should be ready to load the new OS.

---

### Post by orange2k on 2007-09-29
> **alienexplorers said:**
> No matter what program you use to burn the .iso image, make sure you do it at the slowest speed your burner will burn.  Also before burning check the MD5 checksum of the .iso file using:

After you burn the image CD, boot it and use the check disk for errors option to make sure your disk burnt correctly.  After all that you should be ready to load the new OS.

As far as burning speed is concerned, I don`t think it makes much of a difference. The CD will be just as good when you burn it at x52 - no more or less than when you burn it at x1...
I think that only matters when you burn an audio CD, so it would be readable on older CD-players - but on my system, when I burn an audio CD, the burner automatically reverts to x12 instead of x52...

---

### Post by mcduck on 2007-09-29
> **hamishnz said:**
> Ohh thanks for much for that:)
Would anyone be able to explain to me what a ISO file is ?

Thanks Again Hamish

ISO file is a disk image, a file containing not only all the contents of the CD but also exactly the same structure of the file system the burned disk is supposed to have.

[http://en.wikipedia.org/wiki/Disk_image]("http://en.wikipedia.org/wiki/Disk_image")

It's recommended to burn bootable disk images at low speeds (I recommend 4X), as high speed burning easily creates small errors on the disk. These are not a problem with audio disks and such but when it's operating system install disk you'll want every single bit on the disk to be correct.

If you used any other method than the torrent download it's also a good idea to check that the downloaded ISO file is fine, by doing MD5SUM check n it before burning it to disk. In Linux, you can just run 'md5sum filename'. You'll get a sequence of numbers which you can the compare to those available on the Ubuntu download page. This is not usually needed with torrent downloads as the bittorrent protocol automatically checks the files.

---

### Post by bigken on 2007-09-29
all you need to do in ubuntu is right click the iso and select write to disc

---

### Post by SpiritIsReality on 2007-09-29
oops ... my bad ... sorry.
mcduck ... thanks
[http://en.wikipedia.org/wiki/Iso_image](http://en.wikipedia.org/wiki/Iso_image)
buds

---

