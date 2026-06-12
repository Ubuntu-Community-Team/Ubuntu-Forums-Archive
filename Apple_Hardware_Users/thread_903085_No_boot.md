---
title: "No boot"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by brandon333 on 2008-08-27
Installed hardy on intel mac, did everything right, refit is installed, when i boot into hardy i get a no boot found error...HELP!!!

---

### Post by pxwpxw on 2008-08-27
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by brandon333 on 2008-08-28
thanks that worked, got into ubuntu , did updates etc and rebooted now its even wors:

says fdsk error, "disc is in read only mode" then puts me at a command line with an option of ctrl d to exit

---

### Post by cyberdork33 on 2008-08-28
> **brandon333 said:**
> thanks that worked, got into ubuntu , did updates etc and rebooted now its even wors:

says fdsk error, "disc is in read only mode" then puts me at a command line with an option of ctrl d to exit
Are you sure it is "fdsk" ?

It is dropping you to a console. It appears that it is having a problem with your hard drive for some reason. It might be esiest to reinstall at this point, but you can do a check on your disk from the commandline and attempt to repair whatever the problem is. 

First, boot from the Ubuntu LiveCD and open a terminal.
You need to determine what partition your Ubuntu Root partition is:
```
sudo fdisk -l
``` (That is a lowercase L not an i)

This should list all the partitions on the hard drive. You should have one partition that is 'Linux' (not 'Linux swap') and it will have a designation like '/dev/sda3'. Once you determine your Ubuntu partition you can attempt to repair it:

```
sudo fsck -fy /dev/sda3
```

---

