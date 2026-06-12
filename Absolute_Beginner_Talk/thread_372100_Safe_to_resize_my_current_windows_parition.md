---
title: "Safe to resize my current windows parition?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by soul814 on 2007-02-27
I want to install ubuntu on my notebook, do you think it is safe to resize my current windows partition or should i just format the whole thing and set it up from scratch. I just don't want to re-customize my windows partition =/

---

### Post by ddom87 on 2007-02-27
its pretty much safe to resize 
[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by kpkeerthi on 2007-02-27
Make sure you defragment your ntfs partition a couple of times and then use your favorite partition manager to resize it and create free space. I most cases your data should be intact. I did the same and I was OK.

---

### Post by Maestro23 on 2007-02-27
Yes, defrag before you resize.

---

### Post by HasratUSA on 2007-02-27
> **Maestro23 said:**
> Yes, defrag before you resize.

Why is it so necessary to defrag before starting partitioning? I have never defragged my 150 GB HDD in my entire life. Is there anyway I can do that in linux now? I chose ext3 during installation and my distro is Ubuntu 6.10 Edgy Eft.

---

### Post by Maestro23 on 2007-02-27
> **HasratUSA said:**
> Why is it so necessary to defrag before starting partitioning? I have never defragged my 150 GB HDD in my entire life. Is there anyway I can do that in linux now? I chose ext3 during installation and my distro is Ubuntu 6.10 Edgy Eft.

Ext3 file systems don't need to be defragmented.

---

### Post by Cobikegeek on 2007-02-27
Defragging windows filesystems moves all the data to the beginning of the partition so that resizing doesn't obliterate random file fragments scattered across the partition. Resizing can then grab space at the end of the partition with no data loss (usually).

---

### Post by soul814 on 2007-02-27
Yes, I am aware of defragging first, I was thinking the same idea, if I moved everything into the front and then resize it, it shouldnt affect the partition. I was trying to confirm that it works before I gave it a try =] Thanks for all your input

---

### Post by louieb on 2007-02-27
Backup or be prepared to reinstall.  I have resized an NTFS partition 3 times since I started using Linux 9 months ago. 2 went smooth. One well I trashed that windows install ( I also did not defrag that one).
BTW to defrag in XP right click on my computer Manage>Disk Defragmenter.

---

