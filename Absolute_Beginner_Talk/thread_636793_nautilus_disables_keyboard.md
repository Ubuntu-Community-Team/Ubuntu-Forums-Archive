---
title: "nautilus disables keyboard"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-12-10
I switched to openbox instead of gnome. Everything worked fine for a while, but now my external drive doesn't mount on boot. [b]sudo mount /dev/sdb[b] doesn't work for some reason.

```
kernel@laptop:~$ sudo mount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I can only mount it if I start **nautilus --no-desktop** and right click the drive > mount. But If I do that, my keyboard gets disabled in the next 30 min. This really pisses me off because I have to choose either drive or keyboard.

just in case:
**fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=84a23264-023a-492d-bf7f-6a1047ff8cfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2AB02D9BB02D6F0F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=60A0F53DA0F51A6C /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
/dev/sda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb        /media/EXTERNAL\040HD   udf,iso9660 user,noauto,exec 0       0
//HOME-DESKTOP/SharedDocs  /media/SharedDocs  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

---

### Post by rockinlinux on 2007-12-10
that is a really strange problem....i wish i could help you. the only thing i can think of is that maybe its acually a USB issue. is your keyboard USB??

if it is try to mount the disk and while your kepboard is still working post lsusb output.

---

### Post by supersonicdarky on 2007-12-10
it's a laptop so I can't really tell if its usb or not

A temporary workaround that I thought of is to log into gnome first, mount everything there, and then go back into openbox. Won't really work though when I want to plug my flash in though :(

---

