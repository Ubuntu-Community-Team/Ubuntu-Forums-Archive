---
title: "CD Rom got disbled"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by vyas_guru on 2008-02-08
hi... 
i installed wine in my unbuntu7.10 system. then i tried to run the xp setup file using the wine software. after whihc i got some error(at that time i didn't care to see which one). in dat error thr was also an option as debug but i didn't care about it and canceled the error but from dat time onwards my cd rom is not getting detected.
whenever i keep a disk in it, it will not detect teh disk. plz help me out of dis.

---

### Post by jan quark on 2008-02-08
please run and post the output

```
cat /etc/fstab
```

to see if your cdrom drive is listed there

---

### Post by scrooge_74 on 2008-02-08
ok, why you tried to run an xp setup from inside ubuntu?

can you check if you can read the disk or anothe disk somewhere else, you optical reader may be dirty and it could read some disk and not others.

Did you reboot the system at any point?

---

### Post by vyas_guru on 2008-02-08
> **jan quark said:**
> please run and post the output

```
cat /etc/fstab
```

to see if your cdrom drive is listed there

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=f6b065e3-73b1-4ea7-9351-91a87bdc901a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=AEF4DAB6F4DA804F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=b4fd2858-9042-4034-b2aa-848f88806358 /media/sda10    ext3    defaults        0       2
# /dev/sda5
UUID=26E880F6E880C611 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=886002E56002DA38 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=20a5f5e6-b43b-4130-a889-5cb6e5ea4cda /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=f59e78cb-e972-4665-a55f-b934bb724177 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by vyas_guru on 2008-02-08
hey plz help me....
not knowing wat to do....... and i restarted after doing dis

---

### Post by jan quark on 2008-02-08
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

well thats your cdrom it seems to be correct

follow scrooge_74 suggestions and we will see...

---

### Post by vyas_guru on 2008-02-08
i m not able to read any disks

---

### Post by scrooge_74 on 2008-02-10
do you have by chance any bootable CD? of Ubuntu or XP?  Try booting the PC from there at start time? If you can't boot at start time then the CDrom is not reading the disk so it is either dirty or damage.

They tend to get dirty over time and if you don't clean it at some point there is no going back, I have thrown away at least 2 CDROMs in the last 8 years

---

