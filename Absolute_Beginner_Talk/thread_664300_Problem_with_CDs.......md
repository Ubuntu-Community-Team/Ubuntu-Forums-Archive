---
title: "Problem with CDs......"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by abk123 on 2008-01-11
Hi everyone!

I am running edubuntu 7.10 gusty gibbon and windows xp dual boot system.The edubuntu partition is giving error messeges with CDs which contain pics but not to the APT-on-CDrom discs.My windows partiton is working well so there is no prob with the drive hardware...........
I can still get those pics into edubuntu by first loading them into C:\ and then accessing C through edubuntu.

But just curious to know what might be the prob
*_This is what the error messege says_*:
**Cannot Mount Volume**
Invalid mount option when attempting to mount the volume 'UDF volume'

Return for
```
sudo cat /etc/fstab
```

```

abhishek@edubuntu:~$ sudo cat /etc/fstab
[sudo] password for abhishek:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c18c7636-683e-4646-9057-e89e405b95da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=2453407d-76db-4df1-a26e-de1c24389b7e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
abhishek@edubuntu:~$ 

```

return for ```
sudo gedit /etc/fstab
```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c18c7636-683e-4646-9057-e89e405b95da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=2453407d-76db-4df1-a26e-de1c24389b7e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by buccaneere on 2008-01-11
return for [HTML]/etc/mtab[/HTML]???

---

