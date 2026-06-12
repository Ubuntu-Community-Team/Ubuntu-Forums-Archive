---
title: "smbmount with a machine with several disks"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by JoaoCarlosCorreia on 2007-11-05
hi, everybody
I'm running ubuntu 7.04
I'm trying to smbmount a directory with a windows directory in my network.
I'm using the command:
```
sudo smbmount //192.168.1.1/Shared /home/user/folder -o username=my_user,password=my_userpass,uid=1000,mask=000
```
I get this error:

915: session setup failed: ERRDOS - 72
SMB connection failed

The problem is that my windows machine has 3 disks and the directory I want to mount is in P:
If I run the same command to smbmount with another pc in my network with only one disk it works fine.
Could the problem is to "tell" my command which disk is the folder I want to smbmount?

Thanks a lot for any help,

João

---

