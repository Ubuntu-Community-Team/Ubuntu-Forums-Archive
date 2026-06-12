---
title: "Password Protect Drive"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-05-21
I have 2 hard drives on my machine.  The second drive is formatted for linux - I think it is exc3?

Anyway, I've noticed that when I reboot and want to mount this drive, I need to provide my admin password.  If i then un-mount the drive and re-mount it later, I do not require my password.

How would I make it so that the password is required every time the drive is mounted?

Ziffnabb

---

### Post by Cypher on 2007-05-22
The Linux partition format is EXT3. 

The commands "mount" and "umount" require ROOT privileges. So you have to use "sudo" for them, now when you provide your password to SUDO, that information is cached for some time, so subsequence SUDO commands don't require you to re-enter the password.

Usually if you have a Linux formatted drive, you automatically mount it using the /etc/fstab file. Is there any reason you are manually mounting this drive each time??

---

