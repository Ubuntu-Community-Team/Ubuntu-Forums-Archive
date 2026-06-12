---
title: "Can't mount disk ?"
date: 2011-08-02
forum: Any Other OS
---

### Post by sepdau on 2011-08-02
**my fstab**
> devpts     /dev/pts            devpts  defaults            0  0 shm        /dev/shm            tmpfs   nodev,nosuid        0  0 /dev/sda3  /                   ext4    defaults            0  1 /dev/sda1  /mnt/Win7           auto    auto,users,rw,utf8  0  2 /dev/sda5  /mnt/Data           auto    user,rw,utf8        0  2 /dev/sda7  /mnt/Entertainment  ntfs    users,rw,utf8,exec  0  2 /dev/sda6  swap                swap    defaults            0  0[B]
my /etc/group[/B]
 ```

root:x:0:root,bean bin:x:1:root,bin,daemon,bean daemon:x:2:root,bin,daemon sys:x:3:root,bin,bean adm:x:4:root,daemon,bean tty:x:5: disk:x:6:root,bean lp:x:7:daemon mem:x:8: kmem:x:9: wheel:x:10:root,bean ftp:x:11: mail:x:12: uucp:x:14:bean log:x:19:root utmp:x:20: locate:x:21:bean rfkill:x:24:bean smmsp:x:25: http:x:33: games:x:50:bean network:x:90:bean video:x:91: audio:x:92: optical:x:93: floppy:x:94: storage:x:95: scanner:x:96: power:x:98: nobody:x:99: users:x:100:bean dbus:x:81:bean ldap:x:439: avahi:x:84: postgres:x:88: usbmux:x:140: rtkit:x:133: vboxusers:x:108:bean mysql:x:89: gdm:x:120:bean bean:x:1000:bean
```

**I am using account bean.**
**I think I config wrong in fstab and group. Can you help me?**

---

### Post by Barrucadu on 2011-08-02
What exactly doesn't work? Can't you mount it as a user? Does it not mount on boot? Do you get any error messages? What does `fdisk -l` say about it?

---

### Post by sepdau on 2011-08-02
It can't access to folder /mnt/Entertainment and /mnt/Data and /mnt/Win7

---

### Post by kazuya on 2011-08-02
This may not quite apply to you or it may. It is the fastest way I think that can help you. I got all these info from my own troubleshooting in the archbang forum.
 
[http://bbs.archbang.org/viewtopic.php?id=922](http://bbs.archbang.org/viewtopic.php?id=922)
 
The quick solution I would recommend is to
 
pacman -Sy
yaourt -S ntfs-config
Once ntfs-config is installed, you simply call it up from 
System menu > NTFS Configuration Tool
You can then do auto configuration on the ntfs partitions in question. This easily got my problems all solved.
 
You can also try this additionally or prior:
 
pacman -S gvfs
packer -S udiskie
ntfs-3g
hal dbus udiskie ntfs-3g
 
I did nano ~/.xinitrc as root and have this configration below:
!/bin/bash
exec ck-launch-session dbus-launch openbox-session
udiskie &
 
One of these should help you. The NTFS configuration Tool would automagically modify your fstab file accordingly.
 
Folder might be /media/Win7 instead of /mnt/Win7.
 
Goodluck!!

---

### Post by handy on 2011-09-06
> **kazuya said:**
> 
...
 
The quick solution I would recommend is to
 
pacman -Sy
yaourt -S ntfs-config
Once ntfs-config is installed, you simply call it up from 
System menu > NTFS Configuration Tool
You can then do auto configuration on the ntfs partitions in question. This easily got my problems all solved.
...

Thanks kazuya, I just used your method above (roughly;- I use packer for package management, & called ntfs-config via the Terminal 'cause I use Openbox) to get NTFS access to an external USB drive.

The only problem I had was that I had to change the mount point from /mnt/<dir> to /media/<dir> , after that it took a minute or so to get itself organised (adding a line to etc/fstab & such) & Bob's your uncle.

I use Arch/Openbox/Worker, with no icons. When I plug in the drive, Worker pops up a requester asking me if I want to mount & CD to the NTFS drive; I say yes & it lists the contents. If I want to unplug the drive I just hit the eject button on Worker & then unplug it.

Terrific! Thanks again for posting & making it so easy. :D

---

### Post by mips on 2011-09-06
> **kazuya said:**
> This may not quite apply to you or it may. It is the fastest way I think that can help you. I got all these info from my own troubleshooting in the archbang forum.
 
[http://bbs.archbang.org/viewtopic.php?id=922](http://bbs.archbang.org/viewtopic.php?id=922)
 
The quick solution I would recommend is to
 
pacman -Sy
yaourt -S ntfs-config
Once ntfs-config is installed, you simply call it up from 
System menu > NTFS Configuration Tool
You can then do auto configuration on the ntfs partitions in question. This easily got my problems all solved.
 
You can also try this additionally or prior:
 
pacman -S gvfs
packer -S udiskie
ntfs-3g
hal dbus udiskie ntfs-3g
 
I did nano ~/.xinitrc as root and have this configration below:
!/bin/bash
exec ck-launch-session dbus-launch openbox-session
udiskie &


Good post.

I find that a combo of gvfs, fuse, udiskie & ntfs3g will sort out most mounting issues and make your life much easier.

---

### Post by handy on 2011-09-06
I found that my system doesn't like booting up with the USB drive plugged in; it is really slow & throws up errors. As soon as I unplug it the system carries on loading as usual. This doesn't really matter to me, as the disk doesn't need to be plugged in for boot.

I also found that I need to manually run ntfs-config to mount the USB drive, & on checking, the eject commands default settings were having no effect on the USB drive. So I've made left & right mouse button commands in Worker, LMB command: sudo ntfs-config & the RMB command is: sudo umount -v /media/xdisk .

The following eject command also worked: sudo eject -v xdisk , though the umount command seems to be a more efficient (tidier) solution when you look at the verbose output.

---

