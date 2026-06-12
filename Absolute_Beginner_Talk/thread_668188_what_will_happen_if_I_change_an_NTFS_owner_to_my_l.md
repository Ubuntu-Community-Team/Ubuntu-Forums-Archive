---
title: "what will happen if I change an NTFS owner to my linux user?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-15
Hi
thank you for reading my post
What will happen if I issue the following command
```

 sudo chown legolas sda5 -R

```

where sda5 is a folder in media folder and it  somehow show all of my f: when i am in windows.


Thanks

---

### Post by dgray_from_dc on 2008-01-16
The result of that command may change the owner of the mount point or it may not.  I don't think the -R portion will have any effect though.  I don't think Linux can set file permissions on an NTFS volume.

---

### Post by bodhi.zazen on 2008-01-16
Nothing will happen as a result of that command. You can change ownership of the mount point only if the device is not currently mounted, but that will be (re)set when the device is mounted.

For NTFS, ownership and permissions are set at the time of mount

mount -t ntfs-3g /dev/sdxx /mount/point -o uid=1000,gid=1000,umask=007

Or by editing fstab

/dev/sdxx  /mount/point  ntfs-3g  uid=100,gid=1000,umask=007  0  2

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dgray_from_dc on 2008-01-17
Enlightening!!

---

