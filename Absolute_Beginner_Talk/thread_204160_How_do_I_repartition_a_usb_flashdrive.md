---
title: "How do I repartition a usb flashdrive?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Xzallion on 2006-06-26
I was playing around with [DSL-N]("http://www.damnsmalllinux.org/dsl-n/") and decided to try the install to usb drive option.  It repartitioned my flash drive, so that it now has a 95 MB partition and a 150-something-ish MB partition. I want to delete these partitions and format a single partition on the drive, formatting it to work on windows and Ubuntu.  How would I do this?

---

### Post by Jasper Houtman on 2006-06-26
Download gparted or qtparted using add/remove programs.
unmount the flashdrive.
Open g or qtparted and replace the partitions with a fat (32) partition.
open sytem > administration > disks
select the flashdrive, click format and when it's done click enable.

---

### Post by Xzallion on 2006-06-26
Awesome, thanks Jasper.  I really appreciate it. :D

---

### Post by Jasper Houtman on 2006-06-26
Your welcome :)

---

