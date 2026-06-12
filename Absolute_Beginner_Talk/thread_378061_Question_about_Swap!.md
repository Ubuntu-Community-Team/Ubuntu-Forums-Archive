---
title: "Question about Swap!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by HighD on 2007-03-06
Ok, so I succesfully resized my swap partition, but now it doesn't swapon automatically! I need to manually swapon to make my swap functional. Any help on how to make this process automatic?

Now here's my fstab file...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dc78c3f6-3b73-427a-9d24-6bfa5efd1909 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=015B-015C  /media/Music    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=247CC2297CC1F598 /media/MyStuff   ntfs            defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1
UUID=041C4A511C4A3E44 /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=86594304-9e76-460b-b427-93121683b361 linux-swap            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Thanks in advance for your help! :mrgreen:

---

### Post by strikeback03 on 2007-03-06
Here is a thread I started about swap:  [http://ubuntuforums.org/showthread.php?t=373901](http://ubuntuforums.org/showthread.php?t=373901)

Taurus answer at the bottom fixed mine.

---

### Post by Kateikyoushi on 2007-03-06
Replace the uuid part with /dev/sda5 then
```
sudo mount -a
```

---

### Post by taurus on 2007-03-06
This line in /etc/fstab

```
UUID=86594304-9e76-460b-b427-93121683b361 linux-swap            swap    sw              0       0
```
should look like this.

```
/dev/sda5   none   swap   sw   0   0
```
You can edit it with

```
gksudo gedit /etc/fstab
```

---

### Post by HighD on 2007-03-06
Thank you all so much! Tauru's solution worked perfectly! :mrgreen:

---

