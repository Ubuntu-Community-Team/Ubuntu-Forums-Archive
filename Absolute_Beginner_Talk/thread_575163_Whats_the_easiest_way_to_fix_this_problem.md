---
title: "Whats the easiest way to fix this problem?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-10-13
Ive got a dual boot lappie with vista and ubuntu on it, however ubuntu's drive is to small so i can use Disk Management and shrink vista's drive(without dataloss), however I cant add it to Unbuntus drive without deleting it first and losing the possiblity of booting?

So is there a way to uninstall ubuntu without affecting the boot and then installing it later?

Hope this makes sense.

thanks

---

### Post by Pumalite on 2007-10-13
If you are booting with Grub, when you erase Ubuntu, you'll have to restore Vista MBR. Then reinstall Ubuntu. Hope this makes sense.

---

### Post by aysiu on 2007-10-13
Or move /home to a separate partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by defrex on 2007-10-13
You don't need to reinstall Ubuntu. Load up a live CD and use Gparted. It should be able to resize the partitions without data loss.

---

