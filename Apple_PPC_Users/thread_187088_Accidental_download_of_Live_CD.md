---
title: "Accidental download of Live CD?"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by ACoolie on 2006-06-02
Ok, so I went to the download page, selected the first US mirror and chose the .torrent file in the list "http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-powerpc.iso".

So, it finished downloading in like half an hour (<3 Bittorrent), but there is an odd message when I boot the cd. It asks for me to boot as if the CD were a live cd, not an install. I mounted the ubuntu-6.06-desktop-powerpc.iso file and the the CD and it are exactly the same. The md5sums match up. 

Could someone please explain to me what happened here? 
Is it a corrupted torrent file?
Did I somehow burn the wrong one (I checked repeatedly)?
Or, is it meant to be this way and I am supposed to use install from the live cd after it has loaded my desktop?

---

### Post by Jason_25 on 2006-06-02
Yes it is meant to be that way and you install from the link on the desktop.  Much better process assuming the installer doesn't crash.

---

### Post by Ptero-4 on 2006-06-03
ACoolie. You should download the "alternate" iso. It's the old text-based installer. The reason is that the partition tool in the liveCD installer is severely broken (erases irrecoverably the newworld boot partition, fails to recreate it, renders ntf$ partitions useless if you try to resize them, etc).

---

