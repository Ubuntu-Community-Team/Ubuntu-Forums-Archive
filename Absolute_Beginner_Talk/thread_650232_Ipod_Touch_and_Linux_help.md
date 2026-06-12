---
title: "Ipod Touch and Linux help?????"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by lost123 on 2007-12-26
Hi
Im tring to folloe this guide [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
in an attempt to sync my Ipod Touch with Amarok...I finished the section on 'Passwordless Login" but get an error when i log in:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/home/kabi/.ssh/id_rsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /home/kabi/.ssh/id_rsa

and i have to enter the password...so i did this as suggested in the 'If it doesnt work' bit and get this:
#  ls -al ~/.ssh
total 4
drwxr-xr-x 2 root wheel 102 Dec 26 18:25 .
drwxr-xr-x 5 root wheel 204 Dec 26 18:25 ..
-rw-r--r-- 1 root wheel 399 Dec 26 18:25 authorized_keys


Instead of this:

# ls -al ~/.ssh
total 4
drwxr-xr-x 2 root wheel 102 Nov 21 04:25 .
drwxr-xr-x 6 root wheel 306 Nov 20 00:02 ..
-rw-r--r-- 1 root wheel 395 Nov 20 03:01 authorized_keys

I followed the steps correctly and have no idea what going wrong....someone please help

---

### Post by misfitpierce on 2007-12-26
Are you using latest version of Amarok?

---

### Post by lost123 on 2007-12-26
Yes,...but i dont think that should matter at the moment since im just trying to get passwordless login to work

[EDIT]..hmm...i did all the steps again and now it works properly...but ill probably run into more problems later on so ill post back later...

---

### Post by lost123 on 2007-12-26
ok...iv installed ipod-convenience and tried to mount the ipod but now i get this:
$ sudo iphone-mount
Please add yourself to the fuse group, logout/in and try again.
....so i tried ths:
sudo adduser <username> fuse

and loggesd off loged back in and tried agin but the same thing happend 
...any help??

---

### Post by lost123 on 2007-12-26
ok...got it fixed..i just wasnt following the guide properly

---

### Post by HunkieChan on 2008-01-17
how did you fix the problem ? i got the same problem

---

### Post by Kulgan on 2008-02-09
To to the graphical interface for user/group management, click manage groups, select fuse -> Properties, check your username. Then login/logout.

---

### Post by elimisteve on 2008-05-11
In Kubuntu, click the KDE button, then go to Utilities -> System -> Users and Groups.  Click 'Unlock', type in your password, select 'Manage Groups', click 'fuse', then check your user name and save the changes you made.  After you log out and log back in, you will then be a member of the fuse group.

---

