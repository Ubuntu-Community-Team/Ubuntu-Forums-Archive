---
title: "formating"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by greenimacg3 on 2006-12-17
When in ubuntu, how Do I format my HD?

---

### Post by bernied on 2006-12-17
Use the mkfs set of commands
mkfs.vfat
mkfs.ext2
mkfs.ext3

etc

Use man mkfs for details

---

### Post by Bachstelze on 2006-12-17
Or if you want a nice GUI, you can use gparted, which you can install from the repos.

---

### Post by bernied on 2006-12-17
The mkfs commands will 'format' a partition, meaning to build a filesystem. If you want to 'format', meaning to wipe, the drive, use fdisk, cfdisk, gparted, qtparted et al.

Be careful - there are not as many 'this will destroy your system, are you sure?' type warnings as you might find in other operating systems.

---

### Post by bernied on 2006-12-17
gui shmooi

---

### Post by greenimacg3 on 2006-12-17
Uh, I am sorry for my ignorance, but can you tell me exactly howe to format my main HD from inside ubuntu

---

### Post by Bachstelze on 2006-12-17
You mean, the HD where Ubuntu is installed ? Obviously, you can't do it while Ubuntu is running, use GParted on a Live CD.

---

### Post by greenimacg3 on 2006-12-17
Iight, I cannot seem to find my 32 bit live CD.

---

