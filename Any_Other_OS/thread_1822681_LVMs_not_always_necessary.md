---
title: "LVMs not always necessary"
date: 2011-08-10
forum: Any Other OS
---

### Post by tech291083 on 2011-08-10
Hi,

My understanding of LVM partitions is that - only a very few distros such as Fedora need it by default. I am not sure though. I find LVMs a bit difficult to understand. But is it possible to install Fedora using primary partitions? I think it is. Can I install other distros such as Ubuntu, Debian, Gentoo, SUSE and many more using just primary partitions on a single hard drive, making a system with many OS like some people do. Say 5 or 6. Yes, I know that the max no of parititions is 4. 

Please help me here, thanks

---

### Post by boydrice on 2011-08-10
> **tech291083 said:**
> Hi,

My understanding of LVM partitions is that - only a very few distros such as Fedora need it by default. I am not sure though. I find LVMs a bit difficult to understand. But is it possible to install Fedora using primary partitions? I think it is. Can I install other distros such as Ubuntu, Debian, Gentoo, SUSE and many more using just primary partitions on a single hard drive, making a system with many OS like some people do. Say 5 or 6. Yes, I know that the max no of parititions is 4. 

Please help me here, thanks

Yes.[http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/ch-partitions-x86.html]("http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/ch-partitions-x86.html")

---

### Post by FormatSeize on 2011-08-11
> **boydrice said:**
> Yes.[http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/ch-partitions-x86.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Installation_Guide/ch-partitions-x86.html)
Thanks for this. I once mentioned in another thread that Fedora Core forces you to use LVM. Someone told me that it didn't, so I tried to install it with primary partitions. I kind of free-balled it, and didn't really know what I was doing. Some combination of that and it being my first experience with a RAID set up caused things to go downhill pretty fast. I'll follow this guide next time.

---

### Post by el_koraco on 2011-08-11
It only installs to LVM if you do the automated install. If you go manual, it's easy as pie.

---

