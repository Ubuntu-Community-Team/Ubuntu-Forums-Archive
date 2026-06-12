---
title: "501 user/group -- can't read mounted files"
date: 2007-11-17
forum: Apple Intel Users
---

### Post by altonbr on 2007-11-17
So for some reason, /etc/fstab can't mount my HFS+ partition.

I'm using
```
/dev/sda2      /media/osx      hfs     noauto,user,rw  0       0
```
but it's not working.

So I ran this to get it to mount:
```
$ cd /etc/init.d
$ sudo echo sudo mount -t hfsplus /dev/sda2 /media/osx' > bootup.sh
$ sudo chmod +x bootup.sh
$ sudo update-rc.d bootup.sh defaults 
```

The only thing is, the Mac has a uid/gid of 501 and my Linux user can't read the files. Does anyone know how to fix this? I don't want to make the permissions 777.

---

### Post by cyberdork33 on 2007-11-17
> **altonbr said:**
> ```
/dev/sda2      /media/osx      hfs     noauto,user,rw  0       0
```

hfs != hfsplus

> **altonbr said:**
> The only thing is, the Mac has a uid/gid of 501 and my Linux user can't read the files. Does anyone know how to fix this? I don't want to make the permissions 777. You can attempt to make the GID/UID for both systems the same.

Here is a link to a way to make a shared home partition (which I recommend not doing), but it has steps to change the UID/GID for your linux user: [http://ubuntuforums.org/showthread.php?t=486483](http://ubuntuforums.org/showthread.php?t=486483)

---

### Post by altonbr on 2007-11-17
I tried both hfs and hfsplus (sorry, I didn't mention that) and neither worked.

I'll try the tutorial though, thanks! I'm surprised ther is no ntfs-3g-like tool for HFS though.

---

