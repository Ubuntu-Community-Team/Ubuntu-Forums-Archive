---
title: "Running Chkdsk on NTFS Drives Through Ubuntu"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by CeleronXL on 2006-10-09
Hi,

Is it possible to run chkdsk (or a Linux equivalent) under Linux on NTFS drives? It won't run on my Windows drive upon bootup, so I have to find some other way to run it when the drive isn't active.

---

### Post by Mr Frosti on 2006-10-09
Your best bet for this task is using a Recovery Console from a Windows CD. The reason for this is not only chkdisk, but the ability to write back changes to the NTFS partition to correct file system errors.

---

### Post by CeleronXL on 2006-10-09
I tried that, too, but strangely my hard drive isn't detected in the Recovery Console. Same applies with a bunch of other bootable diagnostics. But it *does* work with Linux LiveCDs. I don't get it.

---

### Post by m0e on 2006-10-09
Not sure if this is the answer but is this a SATA drive? Windows CD's don't have SATA drivers so they won't recognize them when running from the CD.

---

### Post by CeleronXL on 2006-10-10
> **m0e said:**
> Not sure if this is the answer but is this a SATA drive? Windows CD's don't have SATA drivers so they won't recognize them when running from the CD.I never considered that--yeah, it is SATA. That explains a lot. Although it doesn't explain why the drive also doesn't show up in BartPE, because I know it works with SATA drives.

Any ideas?

---

### Post by m0e on 2006-10-13
When you first boot from the Windows CD across the bottom of the screen it will ask if you want to load any extra drivers. It will say you have to push F2 or F3 or something like that, then you will have to insert a floppy with your SATA drivers on it. After that I believe you should be able to acccess the drive from the recovery console. the drivers have to be from a floppy, Windows won't recognize an opticle drive at that point so you can't use a CD and I don't think it will read from a USB key either.

---

### Post by tuxcantfly on 2006-10-13
ntfsprogs should have some ntfs checking utility

---

### Post by tuxcantfly on 2006-10-13
ntfsfix, which is a part of ntfsprogs, may be what you're looking for

---

### Post by viper on 2006-10-13
You might want to try Hiren`s Boot CD from this link [http://homepage.ntlworld.com/hiren.thanki/bootcd.html](http://homepage.ntlworld.com/hiren.thanki/bootcd.html)
It has a multitude of tools

---

### Post by tuxcantfly on 2006-10-13
[http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)

might also be useful

---

