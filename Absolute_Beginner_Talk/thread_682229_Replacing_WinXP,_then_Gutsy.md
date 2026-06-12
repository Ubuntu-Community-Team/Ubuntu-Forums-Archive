---
title: "Replacing WinXP, then Gutsy"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Aholiab on 2008-01-29
I have a Sony VAIO with a bad LAN card. I still have a warranty, but I assume that they will not honor it since I wiped the hard drive clean and installed Gutsy Gibbon.

If I have to put WinXP back on (and I just got the DVDs to do this), is there a way to save some kind of image or whatever of my Ubuntu installation? I do have most my data on Jungle Disk and all of my Home folder on an external hard drive. My external is large enough to easily take an image of my system, even the whole thing, if I knew what I was doing.

Any suggestions on how to put WinXP back on (for a new LAN card), then put Ubuntu back on, possible dual booting?

---

### Post by logos34 on 2008-01-29
The easiest thing to do would probably be to use [Partimage]("http://www.partimage.org/Partimage-manual_Usage") to copy root to the external drive.

The only thing you have to do after restoring ubuntu is to [reinstall grub bootloader to the  mbr.]("http://ubuntuforums.org/showthread.php?t=224351")

---

