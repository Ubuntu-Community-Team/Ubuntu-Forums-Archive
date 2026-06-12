---
title: "problems readind data DVD+R"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2008-02-13
I am using Ubuntu 7.10 on my HP Pavilion dv 2500 laptop. I just burned some data on a DVD+R in another computer using Windows (Vista). When I tried reading the data on my laptop I got the following error message:

CANNOT MOUNT VOLUME

Invalid mount option when attempting to mount the volume 'UDF Volume'

Any suggestions to get around the problem?

Aam-aadmi

---

### Post by max renn on 2008-02-13
> **aam-aadmi said:**
> I am using Ubuntu 7.10 on my HP Pavilion dv 2500 laptop. I just burned some data on a DVD+R in another computer using Windows (Vista). When I tried reading the data on my laptop I got the following error message:

CANNOT MOUNT VOLUME

Invalid mount option when attempting to mount the volume 'UDF Volume'

Any suggestions to get around the problem?

Aam-aadmi

Have you seen this link?

[http://www.uluga.ubuntuforums.org/showthread.php?t=510748](http://www.uluga.ubuntuforums.org/showthread.php?t=510748)

---

### Post by aam-aadmi on 2008-03-01
Tried out the suggestion in that link but that does not solve the problem. Here is the output of /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=caa0d91f-4a2d-4fc2-b1ba-e6b1fe674f85 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8c37092-4210-4556-834e-5cca0822938e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Here is the relevant output from dmesg
```
[ 1054.284000] UDF-fs: No fileset found
[ 1214.228000] UDF-fs: No fileset found
[ 1606.704000] UDF-fs: No fileset found

```

Any ideas.

---

