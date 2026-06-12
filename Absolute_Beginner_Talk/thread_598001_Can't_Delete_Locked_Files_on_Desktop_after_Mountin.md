---
title: "Can't Delete Locked Files on Desktop after Mounting .ISO"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Ian222 on 2007-10-30
Recently, I tried mounting a .iso file I downloaded. Foolishly, I mounted it on the desktop. On the desktop, the files I used to have there are not visible and there are two folders with locks on them. I tried installing the software from there, but I had to become root to continue. I got frustrated and tried deleting them but a message came up that said the files couldn't be found. Now there is nothing in the folders, but I can't delete them or see the files on my desktop. 

When I use the terminal, it doesn't see the folders with locks on them, only the original files that were on my desktop. I tried using the terminal to delete these folders, but it says there is no such file. 

How do I get rid of these folders and get to see my other desktop files? Any help would be appreciated.

---

### Post by aktiwers on 2007-10-30
Have you tried deleting through GUI?
```
gksudo nautilus Desktop/
```

In terminal and then delete them.

Or if its mounted folders, use the same command you mounted with, just **don't** write: sudo mount /path/to/mountedfolder...

But use:
```
sudo umount /path/to/your/mountedfolder
```

---

### Post by MrFSL on 2007-10-30
From the terminal what is the output of:
```
mount
```

---

### Post by Ian222 on 2007-10-31
Thanks aktiwers, but that doesn't work. Through the terminal, using gksudo nautilus Desktop/ I can see the old desktop files, but not the folders I want to delete. If I try to unmount, it says: not found. 

The output of mount was:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


Thanks.

---

### Post by Ian222 on 2007-10-31
After I restarted my computer, it was back to normal. Thanks.

---

