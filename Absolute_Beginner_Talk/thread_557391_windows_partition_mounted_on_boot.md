---
title: "windows partition mounted on boot"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by marn on 2007-09-22
I installed Ubuntu last week. The Windows partition (/dev/sda1) is mounted automatically. Can I somehow stop that (isn't that a potential security risk). I've been unmounting it with sudo umount /dev/sda1. Thanks for any help

---

### Post by vikram on 2007-09-22
comment out the line relevant to /dev/sda1 in /etc/fstab file. by inserting a # character at the begining of the line using your favorite text editor. you will require root access.

btw I dont see a security risk here. Am I missing something ?

---

### Post by marn on 2007-09-22
Thanks. Worked fine. As to the security issue: I'm probably just paranoid (just had a windows virus)

---

### Post by Pumalite on 2007-09-22
Intel's Chief Executive said: 'Being paranoid doesn't mean you don't have enemies'

---

### Post by marn on 2007-09-22
@ Pumalite: I'll bear that in mind

---

### Post by kish on 2007-09-22
we play with windows viruses all the time.
How do you think that could affect linuxes?

---

### Post by iansane on 2007-09-22
assuming it's a duel boot and ntfs-3 is installed there is a entry in etc/fstab for that drive.

In the entry after ntfs is the word defaults. 

replace that word with "noauto" and it will not automount.

If you comment out the entry altogether won't that stop you from being able to use "sudo mount" to mount it when you want to, Unless you go back in and uncomment it? I don't know, I'm newbie but it worked for me.

---

### Post by Bothered on 2007-09-22
> **iansane said:**
> If you comment out the entry altogether won't that stop you from being able to use "sudo mount" to mount it when you want to

No, mount can still be used to mount the drive if it isn't in fstab.

---

### Post by iansane on 2007-09-22
cool I didn't know that. Thanks

---

