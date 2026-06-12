---
title: "how to remove permission from a folder and file?"
date: 2007-11-26
forum: Apple Intel Users
---

### Post by collegedude10 on 2007-11-26
i was wondering how do i remove permission from a certain file or folder? im guessing i have to do it through the terminal, just do not know the command.

---

### Post by Bliepo32 on 2007-11-26
How do you mean 'remove permissions'?

You can change the owner of a file with:
```

chown username

```

You can change the group with:
```

chgrp usergroup

```

You can change the permissions with:
```

chmod permissions

```

---

### Post by Grey Box on 2007-11-27
Or, if you don't want to use the terminal, you can use Nautilus (the file browser) and, after right-clicking over the file (or selecting it and choosing File -> Properties -> Permissions) you can change the details.

If you don't have permission to change the file settings, you need to do it as root: 

Type ALT+F2
Type sudo nautilus

Then find your way to the file/folder, and you can change ther permissions/ownership that way.

I find if I need to change the permissions/ownership of lots of files, I use mc (midnight-commander) or gnome-commander. It is a bit more of a hard-core file manager and lets you do lots of powerful things that otherwise would take forever using the regular file browser. Of course if you are a command-line guru, then you can probably get it all done even faster that way.

Cheers

---

### Post by cherry316316 on 2007-11-28
I have mounted my windows drive in 
"/media/c , /media/d , /media/e"
when i goto /media and do ls -l
it gives me 
```

drwxrwx---  9 root plugdev 16384 1969-12-31 16:00 c
drwxrwx--- 22 root plugdev 16384 1969-12-31 16:00 d
drwxrwx---  8 root plugdev 16384 1969-12-31 16:00 e

```

i tried to change the permission, so that the normal user can also use it for read and write
by using command
chmod ugo+rwx /media/d 
and I also tried to change the owner of /media/d by becoming a root.
but its not working.

any idea , how to change the file system permission for windows partition.

Thanks

---

### Post by Grey Box on 2007-11-28
For a windows partition, if you are mounting it in /etc/fstab, you need to change the permissions there. If the windows partition is NTFS, you need to enable NTFS writing as, until recently, NTFS partitions were mounted as read-only. (I googled this and found heaps of tutorials and howtos on the subject).

---

### Post by cyberdork33 on 2007-11-28
> **Grey Box said:**
> For a windows partition, if you are mounting it in /etc/fstab, you need to change the permissions there. If the windows partition is NTFS, you need to enable NTFS writing as, until recently, NTFS partitions were mounted as read-only. (I googled this and found heaps of tutorials and howtos on the subject).
Yes, it is not the folder permission that is the problem, it is that the filesystem is being mounted with permissions that you cannot access.

---

### Post by cherry316316 on 2007-11-28
> **Grey Box said:**
> For a windows partition, if you are mounting it in /etc/fstab, you need to change the permissions there. If the windows partition is NTFS, you need to enable NTFS writing as, until recently, NTFS partitions were mounted as read-only. (I googled this and found heaps of tutorials and howtos on the subject).



Thanks, there was problem with fstab.
I changed the line in fstab from
```

/dev/sda6    /media/e     vfat     defaults,utf8,umask=007,gid=46     0     0

```
to
```

/dev/sda6    /media/e     vfat     auto,rw,users,uid=1000,gid=1000,utf8,umask=000,exec,sync    0    0

```

now, its working fine :)

cherry

---

### Post by Grey Box on 2007-11-28
Great to hear.

---

