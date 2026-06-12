---
title: "Unable to create partitions"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by digitalslavery on 2007-08-01
Hi, I am trying the new version of Ubuntu 7.04 and have been through the set a few times trying to get it installed but I keep running into the same error during the partitioning phase, I figured it might be the hard drive so I reformatted using the windows 98 boot disk and created a partition and rebooted and formatted the drive as instructed then tried to install Ubuntu again and had the same problem. I initially used the Guided option but after it failed I tried manually and still it failed. So I swapped out the hard drive with another one and restarted setup, again the same problem. Rebooted the machine and used the win98 startup disk to delete all partitions and then created a single partition using all the space on the drive, restarted and formatted the drive, restarted Ubuntu setup and still have the same error. Both drives previously had Windows XP them, but that doesnt seem to matter from what I have read so far.

I am not sure what to do next?

Thanks

---

### Post by laidback on 2007-08-01
Maybe you have formatted to a Windows style format which Ubuntu doesn't use. Could you use the clean hdd and let Ubuntu do a standard install with reformatting. It'll probably use ext3 format, which is not available in Windows. (or so I believe) I don't believe it is necessary to format ahead of the install.

---

### Post by bodhi.zazen on 2007-08-01
What version of Ubuntu ?

You might need to revert to the "alternate CD"

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by digitalslavery on 2007-08-01
Version 7.04 - Turns out both of those hard drives were not meant for linux, The third drive I tried worked with out any issues, aside from the random chattering the drive makes, anyway thanks for the suggestions.

---

