---
title: "Cannot Mount DVD after some changes"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bvc310 on 2008-02-01
I was trying to read a data dvd earlier which used the hfs+ filesystem. I was able to do so by entering the following commands into terminal:```
sudo mkdir /media/dvd-ram
sudo mount -t hfsplus /dev/scd0 /media/dvd-ram
```


However, I am now unable to read dvds in any other format. When I try to insert a dvd(it is a commercially produced dvd) into the drive, I receive an error message that the File contents of the folder could not be displayed. Sorry cannot display all the contents of dvd-ram. I tried to run the following command in terminal to try to fix it and received an error:
```

$ sudo mount -t auto /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is mounted on /media/dvd-ram
```

here is a copy of my fstab file as well if that helps anyone. There are a few changes I made that did not work to fix the problem that i have commented out of my fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=fba8591c-517d-4bf5-bc13-4b50acc4f7b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A4488ADF488AB01A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=48F4B378F4B3673A /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=b59be84f-8246-44ff-bd49-8d6d60492535 none            swap    sw              0       0

#/dev/scd0        /media/cdrom0 auto udf,iso9660 user,noauto     0       0
#/dev/scd0       /media/cdrom0   auto user,noauto,exec 0       0
#/dev/scd0 	/media/cdrom0 	hfsplus,iso9660,udf user,noauto 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Thank you for any help it is really frustrating not being able to read dvds

---

### Post by kpkeerthi on 2008-02-01
What happens when you unmount and then mount the device?
```

$ sudo umount /dev/cdrom0
$ sudo mount -t auto /dev/scd0 /media/cdrom0

```

---

### Post by bvc310 on 2008-02-01
Thanks for the reply.
When I run that in terminal with a slight revision:
```
$ sudo umount /dev/scd0
$ sudo mount -t auto /dev/scd0 /media/cdrom0
```
 It works perfectly. Thank you so much for the help. Im not sure why i didnt think of that. It seems so simple. Thank you much for the help.

---

