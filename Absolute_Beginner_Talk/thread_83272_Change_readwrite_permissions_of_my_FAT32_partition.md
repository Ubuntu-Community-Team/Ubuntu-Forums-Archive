---
title: "Change read/write permissions of my FAT32 partition"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by jqp on 2005-10-28
How do I change read/write/execute permissions of my FAT32 (from windows) partition mounted at /media/hdb1/ so that my main user can have full permissions?  Is there a GUI way to do it?  If not, what's the easiest command line way?  I assume it involves "sudo" and "chmod", but I guess I don't know what I'm doing.

---

### Post by Kapre on 2005-10-28
[QUOTE=jqp]How do I change read/write/execute permissions of my FAT32 (from windows) partition mounted at /media/hdb1/ so that my main user can have full permissions?  Is there a GUI way to do it?  If not, what's the easiest command line way?  I assume it involves "sudo" and "chmod", but I guess I don't know what I'm doing.[/QUOTE]

jqp - you can change the permissions in your fstab. You have to use "sudo gedit /etc/fstab" (please check the click on useME on my signature to go to the guide)

K

---

### Post by jqp on 2005-10-28
That helps.  Thanks for the link.

---

