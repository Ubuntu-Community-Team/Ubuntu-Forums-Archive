---
title: "[SOLVED] can't boot into ubuntu"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by planC on 2007-11-03
I have a dual boot system but now suddenly it won't boot into ubuntu, it says '' grub loading, please wait...
error 17 ''   Any ideas? How do I reset the grub loader if I can't boot into  the system?

---

### Post by cotcot on 2007-11-03
Error 17 means that grub finds the partition but does not recognise the file system.
Then you have to look in /boot/grub/menu.list if root is pointing to the correct partition.

I give you an extract drom mine :

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6485392e-a2fe-4709-a013-24e53d0ecd24 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

So root has to point to the partition where the directory /boot with the file /boot/grub/menu.list is on. In my case is is hd0,7 ; this is grubs language for sda8. If it is not correct change it used the liveCD.

If you do not get out of the problem I recommend to follow [[COLOR="Red"]this section[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") the grub manual 

Do you have SATA and IDE drives mixed ? This can confuse grub.

---

### Post by planC on 2007-11-03
I am an absolute beginner. I don't understand any of the things you have sent. I have sent two posts because i didn't know if the first one went. I am using 2 sata drives. All I want to know is how to reset the grub loader, in easy steps, because ' mounting / and /root etc ' are beyond me. Can you help?

---

### Post by cotcot on 2007-11-04
Load the Ubuntu liveCD.
Open the terminal (Applications --> Accessories -->  Terminal)
Check where the boot flag is :
```
sudo fdisk -l
```
This gives something like this 
> cotcot@telenetPC:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24a224a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1  [COLOR="Red"] *[/COLOR]           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8950       30401   172313190    5  Extended
/dev/sda3            8925        8949      200812+  83  Linux
/dev/sda5            8950       10280    10691226   83  Linux
/dev/sda6           10281       11518     9944203+  83  Linux
/dev/sda7           11519       11677     1277136   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008966

Look to the partition with the star in the boot column. Mine is /dev/sda1. (That is where my XP is on). I guess it is the same for you. If it is /dev/sda1 use (hd0), if it is /dev/sdb1 use (hd1) in the grub setup command (see further)

Type ```
sudo grub
```
You will get the grub> preface telling you that you are in grub.
Then ```
find /boot/grub/stage1
```
You will get something like this 
> grub> find /boot/grub/stage1
find /boot/grub/stage1
[COLOR="Red"] (hd1,0)[/COLOR]
grub> 

Then 
```
root [COLOR="Red"](hd1,0)[/COLOR]
```
Remark that (hd1,0) must be the same as what you got with the previous find /boot/grub/stage1
 instruction.
You will get this
> grub> root (hd1,0)
root (hd1,0)
grub> 

Then type
 ```
setup (hd0)
```
Where (hd0) should be replaced by (hd1) if your boot flag is on /dev/sdb1.
Reboot the computer without the liveCD.

---

### Post by planC on 2007-11-04
Thank you, that worked. much appreciated.

---

