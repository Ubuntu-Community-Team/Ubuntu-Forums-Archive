---
title: "Boot problem"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-20
I wanted to make my ntfs partitions to mount at startup. The fstab file from the etc file was initially so: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5 /mnt/captive-local_disc captive-ntfs defaults,umask=none  0 0
/dev/hda6 /mnt/captive-noname captive-ntfs defaults,umask=none  0 0
/dev/hda1 /mnt/captive-noname2 captive-ntfs defaults,umask=none  0 0

```. Now I changed the none with 0222 from the last 3 lines cos' this is what somebody from the forum told me to do. Now I can't boot linux. It stops at Checkin other filesystems (after checking root filesystem and other 2 actions.) Pls heeeeeeelp. I need linux and I don't want to reinstall. I tried to write again none instead of 0222, but nothing

---

### Post by FuzZy2006 on 2006-07-20
I hope anybody could help me soon cos' I have to do something in Ubuntu and the live DVD doesn't have so much possibilities.

---

### Post by adam.tropics on 2006-07-20
Just so you can boot, comment all 3 ntfs lines out, by putting a # at the start. You will probably have to boot the live cd and look around your ext3 partion to do this which will involve

```
mkdir /media/ext3
sudo gedit /etc/fstab
```

add the line
```

/dev/hda3 /media/ext3 ext3 defaults,errors=remount-ro 0 1
```

then in a terminal, type

```
sudo mount /dev/hda3
```

then open nautilus and navigate to /media/ext3/etc/fstab and comment out those lines, and then you should be good to boot up.
Then decide if you need write access to the ntfs partitions, or if read is enough and come back!

---

