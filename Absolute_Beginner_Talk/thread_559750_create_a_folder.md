---
title: "create a folder"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by antonio.segalini on 2007-09-25
I bought an external hard disk Packard bell store and save 3500. my laptop was able to mount it but i can't copy any file inside the hd and so i can't create a folder. How can I do???

Thank you for every suggestion

---

### Post by reckless2k2 on 2007-09-25
get to the terminal and post the results of the following


```
cat /etc/fstab
```

---

### Post by antonio.segalini on 2007-09-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=baf76e39-d1c4-4c5f-8b8b-5ee3da67bbfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=b605ac9c-36a8-42be-b8b1-00d5c4e1be94 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,exec,noauto     0       0

---

### Post by reckless2k2 on 2007-09-25
i assume the drive is not plugged in. if so, can you do the same but for /etc/mtab then.

---

### Post by antonio.segalini on 2007-09-25
it's strange, but the command /etc/mtab tell denies me the permission also in the case if i am the root

---

### Post by tech9 on 2007-09-25
> **antonio.segalini said:**
> it's strange, but the command /etc/mtab tell denies me the permission also in the case if i am the root

try this...

**sudo -i**

enter your password

**gedit /etc/mtab**

make your changes and save \\:D/

---

### Post by antonio.segalini on 2007-09-25
in the meantime I understand that my hard drisk is read only. How can I change this feature?

---

### Post by antonio.segalini on 2007-09-25
the mtab is:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/DATA ntfs rw,nosuid,nodev,umask=222,utf8 0 0

---

### Post by reckless2k2 on 2007-09-25
it's because it's formatted as ntfs. because it's not a permanent mount point, i'm not sure how to get around it. you need the mod that writes to ntfs along with another tweak. there is another work around to format it as ext3 or such. regardless, someone should chime in on the quick and dirty. if it was an fstab mount i could throw it at you easy. i'm sure it is simple. if no one gets around to responding, we can talk about it.

---

### Post by antonio.segalini on 2007-09-25
yes. but how can I format the hd to ext3?? thanks reckless2k2

---

### Post by reckless2k2 on 2007-09-25
i've got to run....i'll be back on a little later. it's pretty easy and doesn't take too long. if no one chimes in i'll pass it too you. once it's formatted, then no fstab mount will be necessary.

---

### Post by nickpaton on 2007-09-25
Found [this post]("http://ubuntuforums.org/showthread.php?t=334795") which explains how to format an external drive from NTFS to ext3.

You may also want to follow [this current post]("http://ubuntuforums.org/showthread.php?t=545287"), where he is having similar problems.

I've found a number of similar posts by doing advanced search and searching - format ntfs -

---

### Post by zhanglini on 2007-09-25
You should read this it will get you write/read permission on NTFS.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

