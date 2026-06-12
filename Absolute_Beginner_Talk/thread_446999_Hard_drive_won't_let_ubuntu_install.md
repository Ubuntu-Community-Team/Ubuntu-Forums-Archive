---
title: "Hard drive won't let ubuntu install"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Tesla1209 on 2007-05-17
I had problems trying to install ubuntu on my hard drive using the live CD. I have run many defragmenters, and I finally used the alternative installer, which said something to the effect of "the hard drive could not be modified" or something like that. It told me to check /var/log/syslog, which I was unable to find. It also mentioned a "virtual console 4". The computer is an older Dell Dimension 2350 with a 60 gb hard drive. Under the live CD, the hard drive (NTFS- I'm not sure if it's necessary or how to change to FAT32) was read-only.

Thanks,
Philip

---

### Post by Bachstelze on 2007-05-17
Use the GParted Live CD to shrink your NTFS partition and then install Ubuntu in the free space.

[http://gparted.sf.net](http://gparted.sf.net)

---

