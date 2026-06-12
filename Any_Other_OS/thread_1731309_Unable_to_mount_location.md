---
title: "Unable to mount location"
date: 2011-04-17
forum: Any Other OS
---

### Post by cdjoya on 2011-04-17
Hey all.

I recently messed around with pysdm and needless to say, I screwed up my system. I now have it up and running, however... I can't access my Windows partition NOR my CD drive for some reason...

After doing some reading, I decided to tackle (I mean edit) my fstab file to accommodate for this... here's the unedited version:

```
    # /etc/fstab: static file system information.
    #
    # Use 'blkid -o value -s UUID' to print the universally unique identifier
    # for a device; this may be used with UUID= as a more robust way to name
    # devices that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc                                       /proc        proc  nodev,noexec,nosuid                    0  0 
    # / was on /dev/sda5 during installation
    UUID=a4880090-4d34-4c42-bf79-0010890be152  /            ext4  errors=remount-ro                      0  1 
    # swap was on /dev/sda6 during installation
    UUID=961c7318-bccc-45a6-bb78-50484ae39ab9  none         swap  sw                                     0  0 
    /dev/sda1                                  /media/      ntfs  nls=iso8859-1,ro,umask=000             0  0 
    # /dev/sda2                                /media/SQ004328V04  ntfs  auto,nls=iso8859-1,ro,users,umask=000,user  0  0  
```

I what I did was simply change the ro in /dev/sda2 to rw, but that didn't change anything...

Oh, and I'm using Linux Mint 9.0 Isadora, dual-booting with Windows 7 (I'm getting rid of it soon!!), on a Toshiba Satellite A205-S4597 laptop.

Any suggestions? Please and thank you! :D

---

