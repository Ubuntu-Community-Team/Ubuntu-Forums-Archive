---
title: "Installing Question"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by scrapqueen on 2007-01-08
I am installing ubuntu on a second internal hard drive. The hard drive is partitioned with space for the OS and space for storage. When I get to select disk I have the options of /dev/hdb:IDE/slave 40.0 GB, /dev/sda:scsii and manually edit. I only want to put the OS on one partition of the hard drive. Do I need to choose to have that done automatically or do I have to manually edit? If I choose to have it done automatically will it use the whole drive or just one partition?

---

### Post by yager on 2007-01-09
You have listed 2 drives and each is being controlled by a different driver controller.  One is an IDE drive and the other is a SCSI drive.  Which drive is the second drive?

When you choose automatic, it will take whichever drive you choose and will divide it up to have a Swap partition and the file system.  If there is no existing system, it will take the whole drive and divide it up.  If there is an existing operating system, it will ask if you want to blow it away or downsize it.

---

### Post by scrapqueen on 2007-01-09
The IDE 40 GB is the second drive which is where I want it to go. The IDE drive already has two partitions on it. When I chose manual it takes me to the screen where I can install in the partitions on this drive and on the c drive (sata). I have to chose a place for the /root and /swap files. If I leave the box for the c drive blank and the one for the second partition blank that means nothing will be written to them correct?

---

