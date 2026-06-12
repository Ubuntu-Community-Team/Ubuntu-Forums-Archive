---
title: "Ubuntu Flash Drive Created for Mac Is &quot;Raw File System&quot; On Windows"
date: 2011-12-10
forum: Apple Hardware Users
---

### Post by asianpowah on 2011-12-10
Hi everyone,

Sorry if this is in the wrong section, I wasn't sure where to put it. Anyways, I recently followed some online instructions and now have a flash drive that has 5 partitions: 1 ext3 grub partition, 1 fat32 partition for my personal data, 1 fat32 partition for my ubuntu installation for mac, 1 fat32 installation for ubuntu and other linux distro installations for windows, and 1 hfs+ partition for the efi bootloader material required for booting on mac.

Now I was hoping that I could boot from both mac and windows based computers (efi vs bios) and could also use the flash drive for other data storage. On mac, it works fine. On windows, however, I can not read any of the partitions and windows tells me to reformat, saying that the file system is "raw."

Going into the disk management tab, I find that the all partitions are healthy and only a 15 megabyte partition (probably either the hfs+ or the ext3, I'm not sure which) is the raw file system (it's shaded whereas all the other partitions aren't); this is probably screwing over everything else so I can't read it.

Therefore, how do I fix the partitions so that windows can read it again as a flash drive, and if I fix them, does this mean I can't boot from mac anymore?

Thank you in advance,

William

---

