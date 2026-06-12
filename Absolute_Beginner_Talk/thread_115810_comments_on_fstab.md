---
title: "comments on fstab"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-01-11
Here is what my fstab output looks like--from a security
or other point of view I would like suggestions on any improvements.


thanks
hc:smile: 


label= / /     ext3              defaults, userqutoa               1            1
label=/boot                      /boot                               ext3      defualts   
none                              /dev/pts                       devpts   gid=5,mode=620
none                             /dev/shm                        tmpts        defaults
none                            /proc                               proc          defaults
none                            /sys                                sysfs          defaults
/dev/hda2                    swap                                swap          defaults

---

