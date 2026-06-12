---
title: "[SOLVED] Access ext3 partition from Leopard?"
date: 2008-06-23
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2008-06-23
Is it possible to access my external usb hdd (using ext3) from Leo?

Thanks.

---

### Post by Nikitas350 on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=619909](http://ubuntuforums.org/showthread.php?t=619909)

---

### Post by cyberdork33 on 2008-06-23
there is a driver, but it does not work that great right now.

---

### Post by PartisanEntity on 2008-06-24
I downloaded the the one from sourceforge and installed it, but did not notice any change, I still cannot access my external hdd.

---

### Post by Kobalt on 2008-06-24
I tried ext2fsx on Leo as well a couple of weeks ago, it wouldn't mount ext3 partitions at all...

---

### Post by owlgorithm on 2008-06-25
This thread is also relevant:

[http://ubuntuforums.org/showthread.php?t=614948]("http://ubuntuforums.org/showthread.php?t=614948")

---

### Post by PartisanEntity on 2008-06-25
Thank you all for the links, it turns out I had installed the wrong version of the Ext2fs driver, you have to install the dev version (at least for Intel based Macs):
[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)

---

