---
title: "LFS will not boot"
date: 2014-01-06
forum: Any Other OS
---

### Post by Tristan_Williams on 2014-01-06
I think the LFS manual should be a little more clear on how to setup LFS to boot.
I don't know what the poop to put in any of the configuration files or anything...
Keep in mind this is the first time I've ever gotten this far in LFS

Heres what I have so far:

In my HOST system:
host is /dev/sda1
Swap is /dev/sda5
LFS is /dev/sdb1

In the LFS system:
/etc/fstab:
```

# file system  mount-point  type     options             dump  fsck
#                                                              order

/dev/sdb1      /            ext4     defaults            1     1
proc           /proc        proc     nosuid,noexec,nodev 0     0
sysfs          /sys         sysfs    nosuid,noexec,nodev 0     0
devpts         /dev/pts     devpts   gid=5,mode=620      0     0
tmpfs          /run         tmpfs    defaults            0     0
devtmpfs       /dev         devtmpfs mode=0755,nosuid    0     0

# End /etc/fstab

```

/boot/grub/grub.cfg:
```

# Begin /boot/grub/grub.cfg
set default=0
set timeout=5

insmod ext2
set root=(hd0,2)

menuentry "GNU/Linux, Linux 3.10.10-lfs-7.4" {
        linux   /vmlinuz-3.10.10-lfs-7.4 root=/dev/sdb1 ro
}

```

Every time I try to boot I get a page of "verbose output" with two really cute penguins on top...
So what do I need to do?

---

### Post by Tristan_Williams on 2014-01-06
Don't worry about helping. I decided I would try Arch, then Gentoo, then MAYBE lfs... when I'm ready

---

