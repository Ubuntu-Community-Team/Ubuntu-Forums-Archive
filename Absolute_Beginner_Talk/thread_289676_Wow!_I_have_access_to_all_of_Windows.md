---
title: "Wow! I have access to all of Windows?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-10-31
I installed Edgy on a drive that doesn't contain the XP installation. I made one ntfs(Windows) ,one fat32(mounted on windows), ext3(root) and some swap space. What do I see after the first boot? All the drives from my Windows installation sitting on my desktop. I can go into the Program Files, look at stuff in my Windows desktop (I haven't actually tried copying/saving). This was not the case with Dapper. Is this something new with Edgy?

Btw, internet is still as bad as it was with Dapper.:)But that's something for another thread.

---

### Post by ReaderRat on 2006-10-31
Far out....Go, man...

---

### Post by _lynX on 2006-10-31
> **navneeth said:**
> I installed Edgy on a drive that doesn't contain the XP installation. I made one ntfs(Windows) ,one fat32(mounted on windows), ext3(root) and some swap space. What do I see after the first boot? All the drives from my Windows installation sitting on my desktop. I can go into the Program Files, look at stuff in my Windows desktop (I haven't actually tried copying/saving). This was not the case with Dapper. Is this something new with Edgy?

Btw, internet is still as bad as it was with Dapper.:)But that's something for another thread.

You can read ntfs, but you cannot write. I'm not sure why you weren't given read access on Dapper. I've had it automatically happen since Breezy.

---

### Post by navneeth on 2006-10-31
I do have a couple of Windows drives that are FAT32. Can I write to those then?

---

### Post by Ben Sprinkle on 2006-10-31
Yes, for NTFS read the HOWTO in the correct section for it.
NOTE: It's not stable and may cause data loss during moving or saving to NTFS.

---

### Post by _lynX on 2006-10-31
> **navneeth said:**
> I do have a couple of Windows drives that are FAT32. Can I write to those then?

You should have no problem reading/writing from/to FAT32 partitions.

---

### Post by givré on 2006-11-02
> **synectics said:**
> 
NOTE: It's not stable and may cause data loss during moving or saving to NTFS.
No more the case since a while. :cool: 
All read/write operation are quite stable now with ntfs-3g :
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Ben Sprinkle on 2006-11-02
Oh, nice. :)
BTW, I am goat spirit and gave up that avatar. :)

---

### Post by PriceChild on 2006-11-02
btw for writing to fat32: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by Ben Sprinkle on 2006-11-02
Can't Linux already write to FAT32?

---

### Post by Leed on 2006-11-02
I could read my Windows partitions on both dapper and edgy.... maybe you just didn't mount your Windows partitions when installing Dapper. I think this should be possible after install using the "mount" command, but I lack the experience to confirm it. 

What also is cool, is that you see Partitions set up by Vendors that are hidden in Windows. I have this on my Laptop. These partitions are mostly used for setting up Windows without CD and with all correct drivers pre-loaded.

---

