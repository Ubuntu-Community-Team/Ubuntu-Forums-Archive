---
title: "Live DVD:HDD doesnt show in &quot;places&quot;"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Janzomaster on 2007-02-18
Hi, I'm checking out Ubuntu with the live DVD and I cant access my HDD! It doesnt show in "places". Both the Partition Manager Tool at "Administration" and fdisk show them. My external usb hdd works fine, the cdrom drive too.

Need help! Thanks

---

### Post by Janzomaster on 2007-02-18
Well, I tried a few things.

First I tried to make the hdd mountable, as described here in method 1, step 2:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

The program opened, but I also got a error message in the terminal:

> ubuntu@ubuntu:~$ gksudo gedit /etc/pmount.allow

(gedit:6614): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I still tried to mount the hdd anyway, with the following command in the terminal:
ubuntu@ubuntu:~$ sudo mount /dev/hda5 /home/ubuntu/Desktop/arf

No response in the terminal after that, but the folder .../arf isnt accessible. I get the error message:
The folder contents cant be displayed. You do not have the permissions necessary to view the contents of "arf".

Any idea?

---

### Post by Janzomaster on 2007-02-20
Ok, no answer to that, next question:

Could this be a live DVD problem? I wanna try ubunutu, and other than the not-mounting, everything seems fine. So, could this be solved if I installed Ubuntu on one partition?

---

