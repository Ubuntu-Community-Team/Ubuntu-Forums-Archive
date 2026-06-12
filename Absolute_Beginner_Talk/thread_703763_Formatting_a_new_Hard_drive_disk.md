---
title: "Formatting a new Hard drive disk"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by obscur156 on 2008-02-21
I have just added a new HDD to my computer,i want to formate it to put only data on it.
I have opened GPARTED and the only option i have is to set DISKLABEL.

The option i have is msdos,amiga,bsd,dvh,gpt,mac ,pc98,s390,sun,loop.
wich one do i choose?
And after that will i be able to format it ???

Thanks for your help guys,best regards.

---

### Post by kinematic on 2008-02-21
Set the disklabel to msdos, after that you'll be able to format it as whatever you want.

---

### Post by LowSky on 2008-02-21
use ms-dos, and if you want the disk to work on other operating systems as well, format it to FAT32

---

### Post by hammad1337 on 2008-02-21
i m confused as to why the ext3 option is not there....
Anyways, from the available options, msdos would be best. you can format it to fat32 and use it on windows systems too, if u ever need to.

---

### Post by kinematic on 2008-02-21
> **hammad1337 said:**
> i m confused as to why the ext3 option is not there....

Because the disklabel is not the same as a filesystem.

---

### Post by obscur156 on 2008-02-21
Thank you guys for your quick reply and i will format it to ext3 of course.
Regards.

---

