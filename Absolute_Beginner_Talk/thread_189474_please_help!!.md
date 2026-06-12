---
title: "please help!!"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-06-05
How do i use my other hard drive on ubuntu? the device manager has recognized it but i have no idea on how to browse it? please assist me.

---

### Post by richbarna on 2006-06-05
[QUOTE=rck_hitokiri]How do i use my other hard drive on ubuntu? the device manager has recognized it but i have no idea on how to browse it? please assist me.[/QUOTE]

Hi rck_hitokiri

Aysiu has a good guide for this on [www.psychocats.net](www.psychocats.net)
Take a look [HERE]("http://www.psychocats.net/ubuntu/mountwindows.php")

---

### Post by arsenic23 on 2006-06-05
Try going to System >> Administration >> Disks

You can use this tool to view or change the location your drives and partitions are mounted too.

---

### Post by steve.horsley on 2006-06-05
You have to "mount" drives before you can browse them.

Open a command-line (Applications->Accessories->Terminal) and enter the command:
> sudo fdisk -l
and post the results here. Also tell us what the "other" drive is, and we'll figure out how to get it mounted for you. 

Also read:
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows)

---

### Post by rck_hitokiri on 2006-06-05
Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1202     9655033+  83  Linux
/dev/hda2            1203        1247      361462+   5  Extended
/dev/hda5            1203        1247      361431   82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3649    29310561    7  HPFS/NTFS

well here it is... how do i mount it ? and one more on you tube i have no sound at all... =(

---

### Post by steve.horsley on 2006-06-05
I assume that by "other" drive, you mean the windows NTFS drive.

Try the following:
First, make a mount point for it with this command:
```
sudo mkdir /media/windows
```

Then edit the file /etc/fstab that defins which partitions to mount at boot-up:
```
sudo gedit /etc/fstab
```
and add this line:
```
/dev/hdb1        /media/windows    ntfs    nls=utf8,umask=222   0  0
```
and save the file. 

Then give the command:
```
sudo mount /media/windows
```
and you should now have access.

This is all as described in [http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) except for the drive name.

---

### Post by rck_hitokiri on 2006-06-05
sudo mount /media/windows
mount: special device /dev/hdbl does not exist


how come it doesnt exist???? what did i do wrong i followed the format? please be patient with me ! thanks

---

### Post by aleskm on 2006-06-05
don't you have a mistake there ? it should be /dev/hdb1 (hdb one) not /dev/hdbl (hdb el)

---

### Post by rck_hitokiri on 2006-06-05
i got it mounted the only prob is on the folder icon there is an x mark on it, how do i deete the folder /media/windows??? please help out =)

---

### Post by gogos on 2006-06-05
Can you clarify, why do you want to remove the directory /media/windows if that is where the drive is mounted?

If you want to unmount the drive and remove the folder you can use the following commands:
```

sudo umount /media/windows
sudo rmdir /media/windows

```

However, the system will attempt to remount the drive when you restart if you added the entry to /etc/fstab.

---

### Post by rck_hitokiri on 2006-06-05
thanks for all the help you guys but there is a problem unmounting the drive....... sudo: unmount: command not found??? what up with this? thanks again.... helpout!

---

### Post by gogos on 2006-06-05
You need to remove the first 'n' in the command, it is just umount (not unmount).

---

### Post by rck_hitokiri on 2006-06-05
the windows folder cannot be opened i dont know why...... there is an x mark on the windows folder... that is why i want to unmount it first then reconfigure gedt.... pleasehelp out....thanks a lot

---

### Post by aysiu on 2006-06-05
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rck_hitokiri on 2006-06-06
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "windows".

what the heck is wrong now??? iver tried anyhting.... someone help?? byt the way some info on my pc is on page 1 you might wanna see it. thanks to all who had the time to help i appreciate it...

---

### Post by dmizer on 2006-06-06
post the contents of fstab
```
sudo nano /etc/fstab
```

---

### Post by rck_hitokiri on 2006-06-06
I WOULD LIKE TO REALLY REALLY THANK ALL THOSE PEOPLE THAT HELPED MY THROUGH THIS PROCESS, MY HARD DRIVE IS 100% okay now.... THANKS TO YOU ALL AND MAY YOU GUYS BE BLESSED!!!!!!! THANK YOU

---

