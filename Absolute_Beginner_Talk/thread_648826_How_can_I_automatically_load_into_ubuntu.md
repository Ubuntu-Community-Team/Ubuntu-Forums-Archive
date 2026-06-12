---
title: "How can I automatically load into ubuntu?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by MONODA on 2007-12-24
Hi I just installed ubuntu over my entire hard drive but kept the recoivery drive in my computer. How can I have it so that my computer automatically loads into ubuntu so that I dont have to select it from the list of oss at grub menu. Also is there anyway to not automatically mount my recovery drive. Thank you for your help.

---

### Post by LaRoza on 2007-12-24
> **MONODA said:**
> Hi I just installed ubuntu over my entire hard drive but kept the recoivery drive in my computer. How can I have it so that my computer automatically loads into ubuntu so that I dont have to select it from the list of oss at grub menu. Also is there anyway to not automatically mount my recovery drive. Thank you for your help.

Post the results of these two commands:

```

less /etc/fstab

```

```

less /boot/grub/menu.lst

```

(If you know what you are doing, you can comment out the line in fstab that is the recovery partition, and you can set the timout in grub to a lower number, and make the menu hidden. If you don't know exactly what to do, I will edit it and post it for you)

---

### Post by Rocket2DMn on 2007-12-24
You need the GRUB boot menu, esp. for emergency situations, like if you have to get into recovery mode or boot to an older kernel.  You can, however, decrease the wait time on it.  Run
```
gksudo gedit /boot/grub/menu.lst
``` and change the "timeout" value to something lower like 5 (seconds).
To stop mounting your backup drive at boot, you need to disable the entry in /etc/fstab:
```
gksudo gedit /etc/fstab
```
Be sure you know which drive/partition it is, you can view all connected drives with
```
sudo fdisk -l
```
Post the output of that command if you have any questions.

---

### Post by ~LoKe on 2007-12-24
```
gksu gedit /boot/grub/menu.lst
```
Scroll down until you see something like this...

> title		Ubuntu 7.10, kernel 2.6.23.11
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.23.11 root=UUID=dd1aef47-fa82-48d7-b594-643a314e8404 ro 
initrd		/boot/initrd.img-2.6.23.11
quiet

It won't look like that exactly, but it'll be close.  Select that whole block and cut it, paste it right under the line that reads:
> ## ## End Default Options ##

Mine would look like this....

> ## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.23.11
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.23.11 root=UUID=dd1aef47-fa82-48d7-b594-643a314e8404 ro 
initrd		/boot/initrd.img-2.6.23.11
quiet

---

### Post by MONODA on 2007-12-24
ok for the first command I got:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=af838259-6b58-4c2a-a9c1-e6737527bdab /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=9ec199ed-a062-4fe2-9306-8cc8c53b8048 /home           ext3    defaults        0       2
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=ff87dd30-7465-4f7d-950e-4254078178c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I edited my grub menu so that the timeout os 2 seconds now is there any way to ignore the recovery partition? Thank you

---

### Post by LaRoza on 2007-12-24
> **MONODA said:**
> ok for the first command I got:

I edited my grub menu so that the timeout os 2 seconds now is there any way to ignore the recovery partition? Thank you

Change it to:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=af838259-6b58-4c2a-a9c1-e6737527bdab / ext3 defaults,errors=remount-ro 0 1
# /dev/sda4
UUID=9ec199ed-a062-4fe2-9306-8cc8c53b8048 /home ext3 defaults 0 2
# /dev/sda2
# UUID=2C88743C8874071C /media/sda2 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=ff87dd30-7465-4f7d-950e-4254078178c1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

---

