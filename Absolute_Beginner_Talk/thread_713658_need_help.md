---
title: "need help"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by RVApunkROCK on 2008-03-03
Quote:
Originally Posted by Jack78 View Post
If you follow this guide you shouldn't run into too much trouble. [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)



installed using this as a guide, but now xp isn't showing up under the OS selection list, how do I get back onto XP?



edit:
selected this option to partition

[IMG]http://apcmag.com/system/files/images/xp_ubuntu_07.article-width.jpg[/IMG]

---

### Post by zabien1970 on 2008-03-03
enter this in a terminal then copy and paste the output
 Open a terminal and type:

sudo fdisk -l (lowercase L)

To open a terminal top left
Applications>Accessories>Terminal

---

### Post by RVApunkROCK on 2008-03-03
isn't 100% as i dont have internet access on the pc with this problem, retyping on a diff pc

Disk /dev/sda: 250.0 GB
255 heads 63 sectors/track 30401 cylinders
units=cylinders of 16065*512=8225280 bytes
Dev Boot  Start    End      Block   ID   Sys
/dev/sda1*   1   29644   238115398+  83 Linux
/dev/sda2          29645   60801002+    5  ext
/dev/sda5          29645   60805714      82  Linux swap / solaris

---

### Post by zabien1970 on 2008-03-03
Oooh, don't look good, the partitions all look like linux (ubuntu), for windows you should have an ntfs partition, you may have wiped windows completely, did you have anything on there you really needed?

---

### Post by RVApunkROCK on 2008-03-03
yeah, tons of music, programs, pictures...

---

### Post by zabien1970 on 2008-03-03
You're gonna want to check out this link
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

---

### Post by bumanie on 2008-03-03
You could probably get test disk and recover your windows information. [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
It is a data and partition recovery program.

---

### Post by RVApunkROCK on 2008-03-03
downloading the iso now, really hope it works, would really suck if I lost all my files, I have tons of PSDs I really need that I hadn't backed up yet :(

---

### Post by RVApunkROCK on 2008-03-03
> **bumanie said:**
> You could probably get test disk and recover your windows information. [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
It is a data and partition recovery program.
the windows or linux version?

---

### Post by zabien1970 on 2008-03-03
Here's another link
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You should burn both cd's and keep them to the side, they're great tools to have in times like these when you need to recover data, I've only used them briefly to recover pics from a camera for a friend but they work and thats what's importantant right now

---

### Post by bumanie on 2008-03-03
> the windows or linux version?
I have the linux version and it searches for both ext and ntfs file systems, so I am not sure what the difference between the two actually is.

---

### Post by RVApunkROCK on 2008-03-03
Ok I've got both burned, just not sure what to do now

---

### Post by antisocialist on 2008-03-03
boot it up like you did the ubuntu livecd, I don't know from there but do that while you wait for them to get back

---

### Post by RVApunkROCK on 2008-03-03
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

done that with the above, theres some kind of command prompt now, no idea what to do from here

---

