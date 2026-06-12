---
title: "&quot;The destination is read-only&quot;"
date: 2010-02-06
forum: Apple Hardware Users
---

### Post by vacancy77 on 2010-02-06
Anyone else run into this problem? I've booted from an Ubuntu Live CD and I've got all the files on my hard drive listed in a window using "gksu nautilus". The iMac I've connected to via Firewire is mounted, along with an external LaCie drive. However, when I try to move any of the files from the hard drive to these volumes, i get "The destination is read-only". These volumes certainly aren't read-only, as they are freely accessed in any direction from from OSX.

Any suggestions?

---

### Post by quixote on 2010-02-07
The destination drives are mounted, but for whatever reason, they've been mounted read-only.  If you right-click on the mounted drive in nautilus (started as gksudo, like you did before), a dropdown menu appears.  Go to Properties at the bottom, and then to the "Permissions" tab.  Maybe it will let you change the permissions to "write" there and the problem will go away.  :)

---

### Post by ichigo on 2010-02-08
Do you know what the format of that "destination" is? If it is HFS+ (the OSX format), there is afaik no write support in Linux. If it is FAT32, NTFS or ext2/3, you should be able to enable write support by changing the permissions.

---

### Post by quixote on 2010-02-08
Good point, re the HFS format!  Actually, there is a utility in synaptic, hfsutils and hfsplus, that's supposed to make it possible to write to HFS+.  I saw it when I was fooling around with a hackintosh, but I haven't used it much.

---

### Post by Megafag on 2010-02-08
> **quixote said:**
> Good point, re the HFS format!  Actually, there is a utility in synaptic, hfsutils and hfsplus, that's supposed to make it possible to write to HFS+.  I saw it when I was fooling around with a hackintosh, but I haven't used it much.

i dual boot OS X and #! linux on my HP desktop, and i could find no way for my linux to be able to write to my mac partition.

OP whynot just back up all of your files to a NTFS external HD, that way both OS's can read from it.

EDIT: actually this might help:

[http://ubuntuforums.org/archive/index.php/t-619909.html](http://ubuntuforums.org/archive/index.php/t-619909.html)

---

### Post by Smelost on 2012-12-24
Actually, use Ctrl+C and then Ctrl+V - works just fine.

---

