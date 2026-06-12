---
title: "lost ubuntu mount point"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-04-08
I installed fprot in Ubuntu 7.04 b6 and lost my mount point. I followed instruction using grub to fix the mbr with the setup(hd0) and the rest of the commands, but it did not restore my mount point. Is there a procedure using the live cd that works?


Thanks, Ratliff

---

### Post by confused57 on 2007-04-08
Here's an excellent guide:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by bratliff on 2007-04-08
Thanks, but the linki will not open. Can you cut and past to this form or me?

Ratliff
[email]robert.ratliff@gmail.com[/email]

---

### Post by confused57 on 2007-04-08
> **bratliff said:**
> I installed fprot in Ubuntu 7.04 b6 and lost my mount point. I followed instruction using grub to fix the mbr with the setup(hd0) and the rest of the commands, but it did not restore my mount point. Is there a procedure using the live cd that works?


Thanks, Ratliff
Is this the method you used to reinstall grub?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bratliff on 2007-04-08
Yes it is. 

Ratliff

---

### Post by confused57 on 2007-04-08
If you get a grub menu at bootup, do you get any error messages when you select an OS to boot?
You might want to boot the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

I'm not familiar with fprot, but after a search found out it was an antivirus program and I don't know how it might have made your system not boot.

---

### Post by bratliff on 2007-04-08
What are the boot loader options when you install Ubuntu 7.04b8? I may not have installed grub. I may have installed anther boot loader. That may be why the grub commands do not work. As you see I know just enough to get me in trouble. How would I determine what loader I am using?

My /boot directory conains:
/boot/abi-2.6.20-12-generic
/boot/config-2.6.20-12-generic
/boot/memtest86+.bin
/boot/System.map-2.6.20-12-generic
/boot/vmlinuz-2.6.20-12-generic


Below is why I become suspicious. 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
cp: cannot stat `/boot/grub/menu.lst': No such file or directory


Ratliff

---

### Post by confused57 on 2007-04-08
Grub is installed by default to the mbr when you install Ubuntu...Do you see a prompt to press "Esc" when booting your computer to access the grub boot menu?

From the link in my first reply, you can probably just copy & paste(except for replacing your actual root partition) and mount your Ubuntu install:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

if grub is installed correctly, you should be able to access your /boot/grub/menu.lst, using the live cd

menu.lst is short for menu.list, not menu.first...just in case that's the problem

---

### Post by bratliff on 2007-04-08
There is no /boot/grub directory. Let me make one and put the menu.1st in it. That seems to be the problem. Where can I find an example of the menu.1st file?

Thank you. Ratliff

---

### Post by bratliff on 2007-04-08
When I boot on the live cd Places show a FIle System and a disk. It seems the old install of Ubuntu is on the disk and the FIle System in on the CD or the CD loaded into memory. I do have the /root/grub and all it's associated files. But when I boot the mount point is missing bad.

Ratliff

---

### Post by ububaba on 2007-04-08
> **bratliff said:**
> There is no /boot/grub directory. Let me make one and put the menu.1st in it. That seems to be the problem. Where can I find an example of the menu.1st file?

Thank you. Ratliff

Apparently I too have lost the mount point

[HTML]rap@rap:~$ sudo mount -a
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad
mount: mount point /media/sdb4 does not exist
[/HTML]

[HTML]
rap@rap:~$ gksudo gedit /etc/fstab
(gedit:6681): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b7c24da-71e3-475f-b98f-3063a34dbf27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=175215a7-e9a9-4a21-b520-aa3772b155da none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1  /media/sda1  ext3    defaults,errors=remount-ro 0       1
/dev/sda2  /media/sda2  none            swap    sw              0       0
/dev/sda3  /media/sda3  ext3    defaults,errors=remount-ro 0       1


/dev/sdb1  /media/sdb1  ext3    defaults,errors=remount-ro 0       1
/dev/sdb2  /media/sdb2  none            swap    sw              0       0
/dev/sdb3  /media/sdb3  ext3    defaults,errors=remount-ro 0       1
/dev/sdb4  /media/sdb4  ext3    defaults,errors=remount-ro 0       1



[/HTML]

[HTML]
rap@rap:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+  83  Linux
/dev/sda2        62910540    83875364    10482412+  82  Linux swap / Solaris
/dev/sda3        83875365   312576704   114350670   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62910539    31455238+  83  Linux
/dev/sdb2        62910540    83891429    10490445   82  Linux swap / Solaris
/dev/sdb3        83891430   293603939   104856255   83  Linux
/dev/sdb4       293603940   625137344   165766702+  83  Linux
[/HTML]

How can the mount point be located when the situation is as above?
Why can't it be found in the first place? Thanks for suggestions/help.

---

### Post by confused57 on 2007-04-08
> **bratliff said:**
> When I boot on the live cd Places show a FIle System and a disk. It seems the old install of Ubuntu is on the disk and the FIle System in on the CD or the CD loaded into memory. I do have the /root/grub and all it's associated files. But when I boot the mount point is missing bad.

Ratliff
You really need to boot up the live cd and post the output of:
```
sudo fdisk -l
```

once you determine which is your root partition, then mount it:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
substitute whatever your root partition is for hda1 in the example

then check the output of:
```
cat /media/ubuntu/boot/grub/menu.lst
cat /media/ubuntu/etc/fstab
```

When you boot the live cd & try to reinstall grub, what does "find /boot/grub/stage1" show as your root partition?
The more info you can provide, the better the chance of someone coming up with a possible solution for you.

---

### Post by confused57 on 2007-04-08
ububaba,
   Looks like you may need to make a directory:
```
sudo mkdir /media/sdb4
```

You could try this first.

---

### Post by bratliff on 2007-04-08
I get the boot menu, but later I get a mount point does not exist msg in the text screen as all the lines scrolll through.

Ratliff




> **confused57 said:**
> If you get a grub menu at bootup, do you get any error messages when you select an OS to boot?
You might want to boot the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

I'm not familiar with fprot, but after a search found out it was an antivirus program and I don't know how it might have made your system not boot.

---

