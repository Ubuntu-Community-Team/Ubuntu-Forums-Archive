---
title: "FAT32 weirdness"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by feap on 2007-01-13
I have an external USB HDD with two FAT32 partitions (didn't have a choice of which file system to format to). Now I'm having weird problem with the other partition (1st, smaller). When I try to open a video file on the partition I get the following message:

"The filename "blaah.avi" indicates that this file is of type "AVI video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system."

The file worked fine on the other partition. If I try to force it open with any video player it won't play ("seek failed") and if I try to copy it to another partition or drive I get "error "I/O error" while copying blaah.." The weirdest thing is that not all files have this problem, just some.

The other partition works just fine and I've never had problems with it.

---

### Post by annda on 2007-01-13
i can't help with the avi/text confusion but the second part of your post reminded me of a problem i've had.

this has probably nothing to do with your problem but still there is a small chance that it may help so i'm posting it: check the file name and make sure it has no special characters. rename the file if that's the case.

if it helps, check your /etc/fstab to see what default character sets your partitions get mounted with.

---

### Post by feap on 2007-01-14
Thanks but it's not that. No special chars and renaming doesn't help.

---

### Post by az on 2007-01-14
> **feap said:**
> 
"The filename "blaah.avi" indicates that this file is of type "AVI video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system."

The file worked fine on the other partition. If I try to force it open with any video player it won't play ("seek failed") and if I try to copy it to another partition or drive I get "error "I/O error" while copying blaah.." The weirdest thing is that not all files have this problem, just some.


The files are corrupt.  Did you power down or unmount the drive before the files were finished writing?

It may also be a hardware problem.

---

