---
title: "Permission Problems with a Mac Hard drive"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by dethredic on 2008-02-15
My friend owns a mac, and he uses an external hard drive to store his pictures, music and other things. His hard drive corrupted and stopped working. He bought another one after many of his attempts were futile. 

So, he brought them both over to my house, I connect them both and boot up. The "broken" hard drive works and I can copy stuff over to my desktop. He wants to transfer all his files over to his new hard drive, but when I drag something (anything) over to the "new" hard drive I get this error:
> You do not have permissions to write to this folder.

So I did this in terminal:
> 
phil@phil:~$ sudo chmod 777 /media/External
chmod: changing permissions of `/media/External': Read-only file system
phil@phil:~$ 


I get the same error as before. The hard drive is formated mac (journaled) but so is the "broken" one so I don't see why this is a problem. Also he set full permissions for everyone.

Does anyone know how I can gain write permissions so we don't have to burn everything to DVD's?

---

### Post by dethredic on 2008-02-15
anyone?

---

### Post by dethredic on 2008-02-15
someone?

---

### Post by dstew on 2008-02-15
Maybe the problem is how you mounted the drive. If it was mounted read-only, I think you might not be able to write to it even if you change the permissions of the mount point directory. How did you mount the drive?

---

### Post by dethredic on 2008-02-15
I pluged in the usb coard into my usb port.

---

### Post by dstew on 2008-02-15
And does it then appear on your desktop? If so, it is being automounted by your fstab file. Post the output of the command```
cat /etc/fstab
```Or, right-click on the drive icon and look at Properties, Volume tab, Mount options. See if it is mounted ro (read-only) or rw (read-write).

Edit: I think actually the mount instruction is in your mtab file, not the fstab file. So, post```
cat /etc/mtab
```

---

### Post by dethredic on 2008-02-15
Yes it automounts on my desktop.

Under the volume tab the mount options reads: ro nosuid nodev umask=22 uid=0 gid =0 nls=utf8

So I assume this is read only.

EDIT: After doing the second command ( cat /etc/mtab ) I get this output:
> /dev/sdb3 /media/External hfsplus rw,nosuid,nodev 0 0

That seems to suggest it is rw.

So, now what?

---

### Post by rfurman24 on 2008-02-15
Are you trying to write to the drive from linux? I do not believe linux can write to hfs+.

---

### Post by dethredic on 2008-02-15
Yes, I am trying to write to it. Both of the hard drive are formatted the same, and I can write to the one plugged in via IDE.

---

