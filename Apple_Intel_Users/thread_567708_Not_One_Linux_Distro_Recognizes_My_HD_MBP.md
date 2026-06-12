---
title: "Not One Linux Distro Recognizes My HD MBP"
date: 2007-10-04
forum: Apple Intel Users
---

### Post by Turnar on 2007-10-04
I am attempting to triple boot OSX / Fedora or Ubuntu / Vista. I have installed OSX and Vista and both are working fine.

Sandwiched between these two partitions is a 25GB space that I would like to drop Linux on to administer a file server. I had originally attempted to install Fedora 7 but stopped when the graphical installer could not find my hard drive. I suspected that it was a problem with either the DVD installer, so I put in my Ubuntu installer that I have used before. It does not recognize the drive either. 

Even if something had gone wrong with my partitioning, shouldn't Linux have still recognized that the drive was there? Please help.

diskutil list output:

#:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Osiris             83.0 GB   disk0s2
   3:   Microsoft Basic Data                    25.0 GB   disk0s3
   4:   Microsoft Basic Data Untitled           40.7 GB   disk0s4

disk0s2 is OSX and disk0s4 is Vista. Both are running fine with EFI.

---

### Post by cyberdork33 on 2007-10-04
Do you have this hard drive?
[http://ubuntuforums.org/showthread.php?t=544626](http://ubuntuforums.org/showthread.php?t=544626)

---

### Post by Turnar on 2007-10-04
Looks to be much the same issue, although different hard drive. Mine is a Western Digital.

---

### Post by cyberdork33 on 2007-10-04
> **Turnar said:**
> Looks to be much the same issue, although different hard drive. Mine is a Western Digital.
Try posting the details in there so that the information is in one place. Nobody has found a solution for that yet (we don't even know what the problem is.) Did you upgrade the drive?

---

