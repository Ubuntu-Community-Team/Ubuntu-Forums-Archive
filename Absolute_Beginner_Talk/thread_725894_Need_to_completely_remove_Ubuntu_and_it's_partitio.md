---
title: "Need to completely remove Ubuntu and it's partition"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Jimm1 on 2008-03-16
I have Ubuntu Gutsy and Windows on the same harddrive. My Ubuntu has completely skrewed up, and I cannot find a way to reinstall it, so my only option is to completely remove it and use Windows instead.
I did the Ubuntu install where it resizes your windows partition, and creates the ubuntu partition. How do I remove Ubuntu, and it's partition, and return my Windows partition back to its previous size?

---

### Post by sandysandy on 2008-03-16
> **Jimm1 said:**
> I have Ubuntu Gutsy and Windows on the same harddrive. My Ubuntu has completely skrewed up, and I cannot find a way to reinstall it, so my only option is to completely remove it and use Windows instead.
I did the Ubuntu install where it resizes your windows partition, and creates the ubuntu partition. How do I remove Ubuntu, and it's partition, and return my Windows partition back to its previous size?

first u must restore windows MBR either thru windows disk or by using Super Grub Disk.

once ur windows MBR is restored u can format ubuntu partition by using gparted or windows CD.

by the way what was ur installation problem.

regards

---

### Post by louieb on 2008-03-16
[URL="http://www.users.bigpond.net.au/hermanzone/p18.htm"]Remove/Replace/Uninstal
[/URL]

---

### Post by Paqman on 2008-03-16
> **Jimm1 said:**
> I cannot find a way to reinstall it

If you've got your disk, you can simply carry out a reinstall as if it were a fresh install. When you get tho the partitioning, choose "manual", and make sure it is formatting your ext3 partition and mounting root (/) there. Make sure it doesn't format any other partitions (except swap, which doesn't matter)

---

### Post by sandysandy on 2008-03-16
here are a few links on dual booting

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)


regards

---

