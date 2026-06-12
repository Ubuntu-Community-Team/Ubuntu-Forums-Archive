---
title: "Mounting issues"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-05-10
Hi
 have a small problem that has been buggin me for a while!
am running dual bool with 3 partitions
sda2 = Vista boot
sda3 = data (common) disk
sda5 = Linux Mepis
sda6 = swap

i mounted my partions by editing the fstab and now looks like this:
/dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda3 /media/common ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5 / auto defaults,noatime 1 1
/dev/sda6 swap swap sw,pri=1 0 0
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ntfs-3g noauto,users 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hda /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0

I can access and both sda2 and sda3 from konqueror though my media folder
but when you go at the storage media folder from konqueror
i can only access sda2 but not sda3 (common)
I also noticed that if i boot from Vista i can see the common sda2 partition, but the files that i ve copied from linux cant be seen, so it looks empty

i am using kde
Many Thanks

---

