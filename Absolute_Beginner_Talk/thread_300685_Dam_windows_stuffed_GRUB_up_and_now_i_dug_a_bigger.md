---
title: "Dam windows stuffed GRUB up and now i dug a bigger hole"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by harrisony on 2006-11-16
Alright i dont need to tell my life story with ubuntu so i wont but in short

i got a win. xp disc and installed it on a seprate partition as i was not paying attension when it changed my active partition to its. it installed..hated windows.

And realised that  i couldnt get to my dapper install armed with my dapper live cd i poked it in and did  some googling and deleted the windows partition and set the active partiton to ubuntu (with some terminal command as i couldnt see it in gparted).

and rebooted then and choose boot from 1st disc and then it said > Error loading operationg system so i went back into  my live cd and here i am now typing this
(note. i can acess my ubuntu partition as i mounted it from the disks option in the system menu

AIM:i want my dapper system back perfect. with no re installing (if possible)
PAYMENT:the joy of knowing you fixed my pc.

Things that may be of intrest
```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19270   154786243+  83  Linux
/dev/sda3           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris
root@ubuntu:/home/ubuntu#


```
```
root@ubuntu:/home/ubuntu# grub-install /dev/hda
/dev/hda does not have any corresponding BIOS drive.
root@ubuntu:/home/ubuntu#

```
```
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu#

```
Anything else you people need?
and thanks a mill. in advance
Also anyone know when ff 2.0 coming to 6.06 reps

---

### Post by Bachstelze on 2006-11-16
You need to mspecify the mountpoint for your Ubuntu partition, like this :

```
grub-install --root-directory=/path/to/mountpoint /dev/sda
```

---

### Post by harrisony on 2006-11-16
errr im a bit confused so if i mounted my partition at /media/moo 
i should run
```
grub-install --root-directory=/media/moo /dev/sda
```

---

### Post by Bachstelze on 2006-11-16
exactly :)

---

### Post by harrisony on 2006-11-16
THANK YOU SO SO MUCH!
i dont know what to say and so quick as well thank you
GO UBUNTU!!! (and its users)

---

