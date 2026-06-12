---
title: "Partitioning Second Drive to use in Unbuntu"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by gambit120 on 2007-12-16
I have installed Ubuntu on a 10gb hdd and am running out of space.  So I added a second physical hdd (40gb) to the system.  When I go into Hardware Info I can see it as a slave drive but I'm not sure how to go about partitioning it. So I downloaded gparted and it sees the disk as /dev/hdb.  I set this hdd to extended partition, but now it says its unallocated. When browsing to my /home folder it still says 5.8gb free - how do I 'see' the second hdd to use it?

I tried once Ubuntu once before and went back to XP but am giving it another shot as I hate Vista.  Have read some of the forums but can't find an exact answer for a noob, hoping someone can quickly solve this for me.

Edit: I don't want to use the second drive for XP/Dual boot but just want to extend hard disk space so I can store some files on it

---

### Post by mikewhatever on 2007-12-16
With Gparted, you can create a ext3 partition in the unallocated space.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

To actually use the partition, you'll have to mount it.
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

