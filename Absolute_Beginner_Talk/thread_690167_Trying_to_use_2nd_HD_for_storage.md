---
title: "Trying to use 2nd HD for storage"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by mcy782 on 2008-02-07
Okay, I'm making progress. My 2nd drive is now showing up in the File Browser as "37.3GB Volume Disk." When I try to access it by clicking on it, there is a file called "lost + found" (I don't have any idea where that came from) When I click on the file, I get the message "Folder Contents Could Not Be Displayed, You do not have the permissions necessary to view the files." I want to make this drive a storage drive for mp3s and such. Any suggestions on what to do next. Thanks.

---

### Post by mikeyphi on 2008-02-07
> **mcy782 said:**
> Okay, I'm making progress. My 2nd drive is now showing up in the File Browser as "37.3GB Volume Disk." When I try to access it by clicking on it, there is a file called "lost + found" (I don't have any idea where that came from) When I click on the file, I get the message "Folder Contents Could Not Be Displayed, You do not have the permissions necessary to view the files." I want to make this drive a storage drive for mp3s and such. Any suggestions on what to do next. Thanks.

You're already successful! You've mounted the drive, got access and found the 'automatically-created' lost & found folder which is system only -no user access!!!
Just go ahead and store whatever you want in your yet to be created folders!!

---

### Post by jan quark on 2008-02-07
please run in terminal and post the output

```
sudo fdisk -l
```

you have to have the permission to access the drive

note that setting permissions to an ntfs or fat formated drives is limited to the time the drive is being mounted
read this for more info

[http://ubuntuforums.org/showthread.php?t=684713&page=2](http://ubuntuforums.org/showthread.php?t=684713&page=2)

---

### Post by mcy782 on 2008-02-08
Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000443f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3557    28571571   83  Linux
/dev/sda2            3558        3649      738990    5  Extended
/dev/sda5            3558        3649      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ac20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081   83  Linux

The sdb1 is showing up in the Computer section and there are mp3 files in a directory. It won't allow me to delete or add files and says "Access Denied: when I try to delete a file or subdirectory. Under "permissions" it says that mike is the owner.

---

### Post by hyper_ch on 2008-02-08
well, you need to chown the mountpoint of the new drive so that you can write to it as normal user. Where did you mount the drive to?

```

sudo chown USER.USER /path/to/mountpoint

```

replace USER with your username
and set the correct path to where it's mounted. Normally it would be in /media somewhere.

---

### Post by mcy782 on 2008-02-08
Thanks. I have it working now. However, somewhere along the line something happened to one of the folders within. I was able to move the folder from the drive to the trash, but it won't delete from trash. It says:

 "Error while deleting. /media/disk/.../Folder.jpg" cannot be deleted because you do not have permissions to modify its parent folder."

  How do I change the permissions so that I can get rid of the folder? Any help would be appreciated. Thanks

---

