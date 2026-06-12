---
title: "Toshiba laptop DVD player"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by schofield0212 on 2007-05-12
:confused: How do you install the DVD player for a Toshiba Satellite laptop? I have downloaded the Windows driver from the Toshiba web site. Simple instructions PLEASE because I am an absolute beginner with Linux and Ubuntu.

---

### Post by Styx on 2007-05-12
post your fstab you can find it here
```
nano /etc/fstab 
```

see if there is a line like the red one

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c2a134ee-b24e-462e-93df-f2221973b9d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9e53f86b-7979-4555-a57b-24488786c802 none            swap    sw              0       0
[COLOR="Red"]/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]


```

---

