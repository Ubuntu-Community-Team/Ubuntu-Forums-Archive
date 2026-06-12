---
title: "Ahh broke my fstab help please!"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by methosb on 2006-06-19
Err I am a complete noob, I wanted to reformat my partition from fat32 to ext3 but forgot that I would have to change the fstab. I tried to change it, it mounts but now I can't write to it and create folders and such, can someone please tell me how I should change my fstab to fix this.

Here is the current fstab the partition in question is **/dev/hdf2**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hde2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hde1 /media/hde1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdf1 /media/hdf1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
**/dev/hdf2 /media/hdf2 ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1**
/dev/hde3 none swap sw 0 0
/dev/hdd /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0

```

here is my old fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hde2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hde1 /media/hde1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdf1 /media/hdf1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
**/dev/hdf2 /media/hdf2 vfat defaults,utf8,umask=007,uid=1000,gid=46,auto,rw,nouser 0 1**
/dev/hde3 none swap sw 0 0
/dev/hdd /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0

```

---

### Post by Jagot on 2006-06-19
To add a Fat32 partition to the fstab so you have read/write privileges it should be something along the lines of:

```
/dev/hda1 /media/windows vfat umask=000 0 0
```

Though of course you'll need to change the hard disk identifier.

---

### Post by [S|G] on 2006-06-19
Have you already formated it? Try to do "ls -l /media/hdf2" and check the owner and permissions. Owner might be root, so you want to change to your user:
```

sudo chown YourUser /media/hdf2 -R

```

---

### Post by methosb on 2006-06-19
thanks S|G all working now :)

---

