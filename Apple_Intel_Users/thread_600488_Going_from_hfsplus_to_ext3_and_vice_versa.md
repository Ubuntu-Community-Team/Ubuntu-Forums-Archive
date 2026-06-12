---
title: "Going from hfsplus to ext3 and vice versa"
date: 2007-11-02
forum: Apple Intel Users
---

### Post by Zaff on 2007-11-02
Hi all.
I was just wondering what would be the easiest way to mount my MacOs Partition under Ubuntu and if there is a way to mount my ext3 partition under MacOS.
I just don't really want to have a FAT32 partition to pass something from one to the other.
It'd be really cool if I could acces both of them regardless of what OS I'm using at the moment. 
Thanks

---

### Post by cyberdork33 on 2007-11-02
hfs+ filesystem support is built into the linux kernel (actually if you look in 'Computer' it should list the detected volumes. double clicking will mount them).

You will not be able to write to hfs+ unless you disable journaling, and then you are still limited by the file permissions.

You can mount ext2/3 partitions in OSX with a utility.
[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)
HINT: get the dev version.

---

### Post by Zaff on 2007-11-02
> **cyberdork33 said:**
> hfs+ filesystem support is built into the linux kernel (actually if you look in 'Computer' it should list the detected volumes. double clicking will mount them).


Yeah I noticed that but there are still diectories that I can't read. and since it's read only I can't change the permissions.

> 
You will not be able to write to hfs+ unless you disable journaling, and then you are still limited by the file permissions.


How do I disable journaling ? Never done that before...

> 
You can mount ext2/3 partitions in OSX with a utility.
[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)
HINT: get the dev version.

Okay thanks I'll check it out.

---

### Post by cyberdork33 on 2007-11-02
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

Also, you need to change permissions in OSX, as some others have found that changing them in Linux does not make them 'stick'.

---

### Post by Zaff on 2007-11-03
This is what I read about ext2fsx_dev but since it seems unstable I don't think I'll be using it yet. When they have a stable solution I'll think about it. And on top of that it doesn't say if it works on Leopard...

> ext2fsx worked great under 10.2.x.  It had read/write support and  
made transferring files between Mac, Windows (read-only), and Linux a  
snap via an external USB/FireWire drive.  Unfortunately, ext2fsx  
didn't work when I upgraded to OS X 10.4.x.  Now ext2fsx supposedly  
works ... sort of:

"1.4d1 is now available from the Files section (ext2fsx_dev package).  
Read only support (for now) and be prepared for kernel panics and/or  
system hangs."

That would be cool if I had a spare Mac, but not on my production  
machine.


Thanks for the help though. If anyone got any experience to share about ext2fsx_dev please let me know. I'm interested.

---

### Post by cyberdork33 on 2007-11-03
> **Zaff said:**
> This is what I read about ext2fsx_dev but since it seems unstable I don't think I'll be using it yet. When they have a stable solution I'll think about it. And on top of that it doesn't say if it works on Leopard...



Thanks for the help though. If anyone got any experience to share about ext2fsx_dev please let me know. I'm interested.
I use it. It works fine. on leopard. I don't mount the ext partitions unless I explicitly need something off that partition.

They are on 1.4d4 now by the way.

---

