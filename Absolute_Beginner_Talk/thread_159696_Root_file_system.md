---
title: "Root file system"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by fgcolin on 2006-04-13
So I am trying to install Ubuntu on my server and it wont let me install it saying that there is 'no root file system defined'. What am I doing wrong? Is there something thats right in my face that I'm missing? Please tell me what to do. Thanks.

---

### Post by Ubuntuud on 2006-04-13
You must have a "/" partition with bootable flag. I guess you are partitioning manually because it is very dificult to get this error otherwise. You should create a partition to install the system on. Select that partition and press enter. There should be a directory name in there (something like / or /home or /var). Select it and press enter. Select "/". Then look for something like bootable or bootable flag, turn it to yes. You should have created a root directory now.

---

### Post by aysiu on 2006-04-13
One of the partitions has to have a "mount point" of /

Yes, that's right--just a slash.

---

### Post by fgcolin on 2006-04-13
Now to up the ante. What if I'm trying to do a RAID with SCSI devices? Same process? Just put a / on the RAID partition? Or does a / need to go somewhere else. Or maybe the process is different altogether. Comments? Anyone?

---

