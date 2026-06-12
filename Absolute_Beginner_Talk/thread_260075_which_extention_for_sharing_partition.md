---
title: "which extention for sharing partition"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-09-18
I've been doing some reading, I want to share a partition between Windows XP and ubuntu - Ive read that ubuntu only supports read support but not write, and that write support is quite risky, also Ive read that FAT32 is a better option. Basically I would like to set up a partition to share data such as music and work between OS's. Thanks in advance

Mike

---

### Post by jd65pl on 2006-09-18
It think that fat32 is probably the best option. It is most commonly used as both operating systems can read/write the file system.

thanks

J

---

### Post by linux_student_user on 2006-09-18
Thanks for your help, another quick question will it mount my partition automaically? can I use it straight away?

---

### Post by Obor on 2006-09-18
Another option is to use ext3 on your shared partition (same filesystem as ubuntu) and install [FS driver]("http://www.fs-driver.org/") in windows to recognize it. You'll be able to read and write to it in win as well

---

### Post by Brunellus on 2006-09-18
> **linux_student_user said:**
> I've been doing some reading, I want to share a partition between Windows XP and ubuntu - Ive read that ubuntu only supports read support but not write, and that write support is quite risky, also Ive read that FAT32 is a better option. Basically I would like to set up a partition to share data such as music and work between OS's. Thanks in advance

Mike
The safest option is FAT32:  it's well-understood and is fully supported by both the Windows NT and Linux kernels.

---

