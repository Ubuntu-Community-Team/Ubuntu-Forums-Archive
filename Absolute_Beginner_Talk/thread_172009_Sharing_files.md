---
title: "Sharing files"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by zudduz on 2006-05-07
How should I share files such as pictures and music between users?
How should I share files to windows computers on my network?
I would like these to remain secure.  Is it easy to deny access to users that haven't authenticated.

---

### Post by stinkypudding on 2006-05-07
Try Hamachi:

[http://www.hamachi.cc/](http://www.hamachi.cc/)

---

### Post by WolfJay_83 on 2006-05-07
There are plenty of ways of sharing files as ubuntu supports just about any protocol.  You can set up nautilus to access windows shares from the toolbar, or set up your own ftp server with proftp.  

Allot depends on exactly what you want.  ftp will give you the most security, while allowing you to set different permissions, versus windows shares are sometimes more convenient.

Are you planning on sharing between many computers on a local network? or the internet? Do you want to be able to give certain people more privlidges (eg. read/write) than others?

For reading about file sharing, try the wiki at [https://wiki.ubuntu.com/FtpServer](https://wiki.ubuntu.com/FtpServer)
[https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare](https://wiki.ubuntu.com/LucasArruda/ConfiguringEasyUnauthenticatedSambaWindowsLinuxShare)

If you want to mount remote partitions just like local partitions on linux/mac/unix machines, you can use NFS
[https://wiki.ubuntu.com/SettingUpNFSHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo)

---

### Post by nalmeth on 2006-05-07
samba works good for sharing with windows computers
right-click the folder, and click share
or share options
or something similar 
:D

as for sharing between users, just right-click the folder, go to properties, and dictate the permission's you want to allow.

---

