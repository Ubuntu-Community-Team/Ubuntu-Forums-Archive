---
title: "How to keep the permissions of files when they are copied to USB?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-11-09
Whatever the permissions of files are, permissions are changed if files are copied to USB drives.

I have two USB
"sudo fdisk -l" shows that
one is "W95 FAT16 (LBA)" and the other is "W95 FAT32 (LBA)".

Files of "W95 FAT16 (LBA)" are always drwx------ 
and
those of "W95 FAT32 (LBA)" are always drw------- .

How can I keep original permissions of files ?

---

### Post by SpiritIsReality on 2007-11-09
howdy
edit: this is not the answer. Please see the following posts.
(Try the last paragraph of 4.5 here. It's supposed to work.
 [http://rute.2038bug.com/node7.html.gz#SECTION00750000000000000000 )]("http://rute.2038bug.com/node7.html.gz#SECTION00750000000000000000")
all the best
trails

---

### Post by hyper_ch on 2007-11-09
if you copy to fat32 you can't keep the permissions as fat32 doesn't use linux file permissions.

---

### Post by insane_alien on 2007-11-09
format that drive as ext2/3 or reiser or JFS that'll let you preserve permissions though compatability with windows/mac systems will be lost unless the have appropriate drivers

---

### Post by hyper_ch on 2007-11-09
there are ext2/3 drivers for windows... dunno about reiser or JFS...

another option would be to tar.gz the files and copy the archive. When you untar the archive again on a linux filesystem the permissions stay intact.

---

### Post by Trebaruna on 2007-11-09
...but then you have to have some software to be able to extract the archive, if you want to use it with windows.

---

### Post by hyper_ch on 2007-11-09
Total Commander can handle tar.gz files easily... but still the problem lays with the filesystem.

---

