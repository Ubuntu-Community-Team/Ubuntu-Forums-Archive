---
title: "Configuring new XFS partition"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by [S|G] on 2006-05-26
Hello, 

Today I decided I didn't need M$ windows on my computer anymore, and formated its partition as XFS. Everything went nicely, but when I mount it on /home/diego/Arquivos (its a sub-directory inside my home folder) it has root as owner. What should I do? I tried to sudo chown -R diego /home/diego/Arquivos but that didn't work.

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda5 / reiserfs defaults,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda2 /boot reiserfs notail,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda4 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda6 /home/fs/dos vfat defaults,umask=000 0 0
/dev/hda1 /home/diego/Arquivos xfs defaults,atime,auto,rw,dev,exec,suid,nouser 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Thanks!

---

### Post by Sef on 2006-05-26
How did you delete Windows?

---

### Post by [S|G] on 2006-05-26
My windows was in /dev/hda1, as you can see. I first unmounted the device then deleted the partition using fdisk. In the empty space I created a new XFS partition. It was working right after writing changes to disk :)

I re-installed grub to /dev/hda1 to make sure the system would boot again, even before trying to reboot.

Also, I managed to fix the permission problem. I chowned it again and on the second time it worked (probably I did something wrong on the first :?)

---

