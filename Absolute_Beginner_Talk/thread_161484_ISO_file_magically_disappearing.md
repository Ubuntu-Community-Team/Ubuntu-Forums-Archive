---
title: "ISO file magically disappearing"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-17
Yesterday I tried to mount an ISO file:

mkdir /mnt/iso
sudo mount -o loop /path/to/file.iso /mnt/iso/

I started pasting files from the ISO onto my desktop. The file icons had a "lock" emblem. I soon found out that it was the same as when copying files from a CD in Windows, they keep the read-only attribute that they had on the CD.

However, after five trouble-less minutes, I was suddenly unable to copy files from the ISO. The system reported something like: "I/O Error: Unable to read file.". I was able though, to browse through the ISO file, but all the files were 0 bytes long. So I checked my USB drive (as the ISO was mounted from there). There was nothing wrong with it. I "umounted" the ISO, copied it to my desktop and mounted it again. Ta-da: I could copy files from the ISO again. But not for long: after some other five minutes, I was receiving the same error.

I am desperate. Why does Ubuntu does this to me?

---

### Post by YuHoo on 2006-04-17
I've had similar problems on my Win2k computer using Deamon tools to mount and manipulate .iso. In those cases I found that it was the iso file that was corrupted and would produce the exact same result as you have. I'd suggest you retry downloading the iso file (ISOs are a 50/50 for corruption due to their size it increases the probablility something wrong will happen).

---

