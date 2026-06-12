---
title: "/home to a new partition?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by bhoughton on 2006-07-31
Hi,

I have read that it is best to set up /home on a seperate partition but want to know if it is possible after Ubuntu has already been installed?

I have GParted installed, and it tells me that on my hardrive (20GB) there is dev/hda1 ext3 17.93 GB (boot), dev/hda2 extended > dev/hda5 (729MB).

Also, is it possible to allocate around 5 GB of the dev/hda1 partition for another install?

Regards,

---

### Post by Paerez on 2006-07-31
Yes, just right-click on the /dev/hda1 partition and you can resize it. Choose how much "free space after" the partition you want, and it will make a chunk of free space. You can then make a partition in that free space and format it, then mount it as home.

Then you can make another partition in the free space for another installation.

---

### Post by teasum on 2006-07-31
Check out this howto: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html).

Also, see this thread: [http://www.ubuntuforums.org/showthread.php?t=213623](http://www.ubuntuforums.org/showthread.php?t=213623).

One possible problem is that all the configuration files might not copy over completely.  When I moved my own /home to a new partition, most of my settings reverted back to default.  I solved that easily, however, by copying each settings folder over manually, which was very easy.  Good luck!

---

