---
title: "Editing /etc/fstab"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by deranged on 2008-01-01
hi, i'm a new user of ubuntu, and would like to mount my usb devices automatically when i plug them in. i've been trying to edit my /etc/fstab, but to no avail. i searched around, and this command in terminal worked for me:

```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sda1 /media/usbdrive
```

is there anyway i can transfer this command into my /etc/fstab? thanks!

---

### Post by Irony on 2008-01-01
It should mount automatically anyway.

Look at;

```
System > Preferences > Removable Drives and Media
```

Check that in the Storage tab that the first 3 items are ticked.
_________

Note that you can also issue the command;

```
sudo mount /dev/sda1 /media/usb
```

To mount your drive - this assumes that you have made a directory called usb in media.

---

### Post by deranged on 2008-01-02
ok, can, thanks, i'll go home and try it out. =) thanks

---

### Post by deranged on 2008-01-02
> **Irony said:**
> It should mount automatically anyway.

Look at;

```
System > Preferences > Removable Drives and Media
```

Check that in the Storage tab that the first 3 items are ticked.
_________

Note that you can also issue the command;

```
sudo mount /dev/sda1 /media/usb
```

To mount your drive - this assumes that you have made a directory called usb in media.

hi, the first 3 items in the storage tab are ticked, but no, my disks still don't mount automatically.

it says that there is a bad file system in /etc/stab or something like that.. i'm not very good in ubuntu and it's errors yet, =X so i really need help thanks, haha. =)

---

### Post by thelatinist on 2008-01-02
Please post the results of:

```
sudo cat /etc/fstab
```

---

### Post by marx2k on 2008-01-02
Here is my USB mount for fstab but I am not sure if this is in here as an afterthought because of Virtual Box... 
```

none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

```

---

### Post by deranged on 2008-01-03
sudo cat /etc/fstab shows the following:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3df59da2-b9fe-4958-946f-892889311f1e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=42bcf67a-42d7-4d9a-ac6a-bb484ae955b8 none            swap    sw              0       0

/dev/sda1       /media/usbdrive         auto    user,no,auto                   0       0
/dev/hdc        /media/cdrom1                   udf,iso9660 user,noauto,exec   0       0
/dev/scd0       /media/cdrom2                   udf,iso9660 user,noauto,exec   0       0

i dun think i have virtual box.. if i do then i dunno how to use it.. lol

---

### Post by philinux on 2008-01-03
Just plugged my usb stick in and it shows up as /dev/sdc

I have no mention of that in fstab and it mounts when plugged in.

---

### Post by deranged on 2008-01-03
> **philinux said:**
> Just plugged my usb stick in and it shows up as /dev/sdc

I have no mention of that in fstab and it mounts when plugged in.

this was the part that helped; turned out that there was no need to have anything in /etc/fstab

thanks to all who helped in some way or other! :popcorn:

---

