---
title: "permission"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-28
I keep running into problems writing to folders (my usbdisk for example). It says "you do not have permissions to write..etc. Well, if I am sudoer and part of the root group, what else do I need?

---

### Post by po0f on 2006-10-28
saintj0n,

Do you know what the /dev entry for the usb stick is?  Just `ls -l /dev/usb_stick` and see what group owns it, and add yourself to that group (if the group has write permission).  Might be the plugdev group.

---

### Post by hearnden on 2006-10-28
Fixing the users and groups on the folders, mount points and /etc/fstab entries will probably fix your problem.

Another less likely cause is that the folders do not have write permissions enabled (use 'chmod u+w myfolder' to fix).

---

