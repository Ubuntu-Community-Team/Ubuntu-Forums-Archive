---
title: "Drive not recognized"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by rlinsurf on 2010-01-24
Hi--

I have a Mac Pro 3,1 with 4 bays. In bay 1 I have a 2TB sata drive, which is showing properly. In bay 3 I have my Mac 1TB hfs+ 10.6.2 hard drive. In bay 4 I have a partitioned 1 TB drive, which has my mac's backup of about 850GB HFS+, and my Ubuntu system volume.

In bay 2 I did have another 1TB hfs+, but I replaced it with a drive I need to copy, a 320GB sata drive with 3 partitions, one of them being xfs.

However, when I boot from the ubuntu CD, and check the partitions, sdb shows as a 1TB hfs+!

Why isn't ubuntu recognizing my drive?

Can somebody help? I.e., is there a way to check the partitions within ubuntu proper, and not necessarily the cd?

---

### Post by rlinsurf on 2010-01-24
Well, I figured it out. Apparently, the drive wasn't securely connected. It's now showing up.

However, even though it's in bay 2, it's showing as sdc, and the drive in either 3 or 4 is showing as sdb. Am I just missing something obvious again?

Thanks :)

---

