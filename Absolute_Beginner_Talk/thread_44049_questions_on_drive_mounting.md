---
title: "questions on drive mounting"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by lordmcdra on 2005-06-24
This question has been removed and relocated to an approriate section.

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=lordmcdra]I have a question about mounting drives.  I used the command *sudo mount /dev/sda5 /mnt/Zero -t ntfs -o umask=000* to mount a particular hard drive but I have read only access as a basic user.  How do I change the drive from read-only access to write access.[/QUOTE]
 Linux can't write to NTFS filesystem. It is just not supported - nothing you can do by changing mount options. There are good reasons for it (search via google), and there are some experimental patches that try to enable NTFS write, but they are risky. 

If you need to exchange data between Windows and Linux, I suggest creating a separate FAT32 parition.

---

### Post by desdinova on 2005-06-24
NTFS is a MS filesystem that they haven't released the specs on, (to lock us out basically) and so NTFS support by default is only read-only - there is some experimental write support for NTFS but it is that - experimental

---

### Post by lordmcdra on 2005-06-24
thank for the help

---

