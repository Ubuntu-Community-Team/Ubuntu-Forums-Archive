---
title: "HFS Bootstrap? Can't install!"
date: 2006-11-16
forum: Apple PPC Users
---

### Post by Ububurns on 2006-11-16
Yikes.

I've been trying to install Edgy on my sister's iMac:

"No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system."

I can't get past this error message!

(I had no problems putting it on my own iMac...)

---

### Post by Ububurns on 2006-11-16
Went into GParted, reformatted the small "unknown type" partition listed there to HFS, with a boot flag. If all goes well, I think it will work.

Thanks to the two people who read this post before I found a solution...

---

### Post by Kalvin on 2006-11-17
If that doesn't work you'll need to use the Alternative Install CD as the DesktopCD partitioner cannot create the NewWorld partition.  The Alternate Installer can, however.

---

### Post by ixus_123 on 2006-11-18
Cheers - that might help me.  I couldn't get it done & so couldn't partition my drive - I was able to do an auto install though but apart from swap, the installer didn't delegate any partitions.

---

### Post by Kalvin on 2006-11-20
You'll need to manually set up the partition table.  Sorry, should've mentioned that earlier.  Also make sure to leave a small amount of free space at the end of your drive.  I understand that Apple hardware may need that to boot from a drive.

Hope it helps.

---

### Post by samden on 2006-11-24
How are you getting on with this? I would be interested in hearing whether you get it installed or not. I am having similar errors installing to an iMac G3 (trying many different flavours of linux to no avail, all different errors but mostly related to dbootstrap).
(the ongoing saga of my struggles:
[http://www.ubuntuforums.org/showthread.php?t=300122](http://www.ubuntuforums.org/showthread.php?t=300122))

---

### Post by djmoksha on 2007-12-27
im having the same exact problem as OP,

can't get past this, i cant boot an alternate install cd either, im trying to install on an orange iBook.

---

