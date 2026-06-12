---
title: "Ubunto 7.04 Freezing on Install - Powerbook G4"
date: 2007-07-03
forum: Apple PPC Users
---

### Post by 0graham0 on 2007-07-03
I've been trying to install Ubuntu on a Powerbook G4 17". 

Originally I tried a guided partition and the install would freeze when trying to create the ext 3 file system. I then followed Syclonemedia's instructions for partitioning the hard drive at [http://ubuntuforums.org/showthread.php?p=2959132#post2959132](http://ubuntuforums.org/showthread.php?p=2959132#post2959132) . One thing I did differently: When partitioning and installing Mac OS X, I created a 40 gigabyte partition for OS X, and left 15 GB as free space. I then created partitions using GPartEd.

Now the installation moves beyond the partitioning, but freezes at 27% when it is supposedly "Copying files." The CD drive stops spinning as well as the Hard Drive.

Any suggestions would be greatly appreciated,
thanks

---

### Post by tgalati4 on 2007-07-04
Did you check the MD5 sum using the "Check CD" routine under the Options menu?  It's possible that you have an error on the CD that is causing the hang up.  The MD5 sum forces a read of the entire disk.  If the checksum doesn't match what's advertised from within the README file then you know you have to burn a new disk.

This is a frustrating error because you can't view the log files.  It looks like a file copy or file read problem.

Good luck.

---

### Post by pxwpxw on 2007-07-04
From a terminal in  MacosX you can see if there is any problem with the partitioning using pdisk
```

 sudo pdisk -l

```

---

