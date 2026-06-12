---
title: "[SOLVED] chmod &amp;amp;amp;amp; directories"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-10
Can someone tell me what the procedure is to change the permissions on a usb drive to allow it to be used to hold backup files. sbackup says it can't write to it.

---

### Post by hardyn on 2007-01-10
chmod 777 -r /dir/sub/sub?

is that what you had in mind?

---

### Post by squrl on 2007-01-10
I have a usb drive that is mounted as /dev/sdb1     /mnt/v1

I want to park backup files on it but the prog says it can't write to that drive. 
Is there anything I can do to it to make it acceptable

---

### Post by szf on 2007-01-10
There isn't a 'read-only' switch on that usb drive, is there?

Otherwise post this output here:
```

$ ls -ltA /mnt

```

---

### Post by taurus on 2007-01-10
You cannot use chmod to change permissions if it's a ntfs or vfat/fat32.  You have to mount it with the right permissions either from a terminal or through /etc/fstab.

---

