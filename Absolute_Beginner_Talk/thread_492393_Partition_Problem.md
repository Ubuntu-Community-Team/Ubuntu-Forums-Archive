---
title: "Partition Problem"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by All_Al on 2007-07-04
For some reason, all my partitions are read-only outside of the "file system" partition.  I downloaded qtparted and tried to reformat the partitions, but it just blanked them out, now when I try to adjust the partition it only offers me the property icon(which does me no good).  I need the drive mounted, cause I need the space.  I also need to switch a old windows NTFS partition out of read-only.

---

### Post by limbourg31 on 2007-07-04
if you're trying to write to an NTFS partition use the ntfs-config tool, sudo apt-get install ntfs-config

this link might be useful [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-config+howto](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-config+howto)

---

### Post by gn2 on 2007-07-04
Best way I know of making and NTFS partition writeable is with the AutoMounter available through [www.getautomatix.com](www.getautomatix.com)

It's in the Miscellaneous category once installed.

Automatix has it's own support forum, should you require assistance with it for whatever reason.

---

### Post by Bothered on 2007-07-04
I have found ntfs-3g (configured by ntfs-config) works very well.

---

### Post by theDaveTheRave on 2007-07-04
Chekc out this forum as well.

[HTML]http://ubuntuforums.org/showthread.php?t=217009[/HTML]

I've followed the instructions and can now read and write to the HD partition holding vista... although I am yet to be able to patition this partition....

I'll get there soon though.!

Dave

---

