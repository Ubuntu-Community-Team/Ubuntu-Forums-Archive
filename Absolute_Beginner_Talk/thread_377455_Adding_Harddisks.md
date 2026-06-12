---
title: "Adding Harddisks"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by weightgain4000 on 2007-03-06
Hello,

Im currently running ubuntu from a separate hard disk on my computer, I run windoze on my other hard disks.

I would like to be able to access the files on my windows disks

I tried to use this guide to add my disks but it didnt work

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I got as far as  "sudo mount /dev/sda1 /media/Windows Drive" 

whenever I use this command all I get is a list of all the flags for mount! :confused: 

Any help would be greatly appreciated

Thanks

John

Resolved 

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

### Post by cookfromfrozen on 2007-03-06
You probably need quotes around the mount point path, try this:

```
sudo mount /dev/sda1 "/media/Windows Drive" 
```

or just try "/media/Windows"

make sure the directory "/media/Windows Drive" exists, if not you can create it with

```
sudo mkdir "/media/Windows Drive"
```

---

### Post by weightgain4000 on 2007-03-06
Great! that worked!

However now when I try and view the drive in the media folder is says I dont have permission to view it :P

---

