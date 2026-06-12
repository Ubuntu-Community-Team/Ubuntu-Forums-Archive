---
title: "Need help with smbfs"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by SimzI on 2006-07-07
Hi, I'm trying to mount a network folder so that I can play mp3 in my xmms.

root@ubuntu:~# mount -t smbfs //rickserver/ //rickserver/Server-D/mp3/
mount: mount point //rickserver/Server-D/mp3/ does not exist

I kepp getting told the location doesn't exist. Can anybody help me?

:D Thanks.

---

### Post by SimzI on 2006-07-07
Ok, I figured out I Was using the wrong syntax etc..

root@ubuntu:~# mount -t smbfs //rickserver/Server-D/mp3 /home/rick
mount: wrong fs type, bad option, bad superblock on //rickserver/Server-D/mp3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What's a "superblock" ?

---

### Post by SimzI on 2006-07-07
I realised smbfs wasn't installed, so I installed it.
However, I'm now getting a different error message:

rick@ubuntu:~$ sudo mount -t smbfs //rickserver/Server-D/mp3 /home/rick
Password:
18378: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

---

### Post by echo $USER on 2006-07-07
> **SimzI said:**
> I realised smbfs wasn't installed, so I installed it.
However, I'm now getting a different error message:

rick@ubuntu:~$ sudo mount -t smbfs //rickserver/Server-D/mp3 /home/rick
Password:
18378: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
Try mounting it using the ip address of rickserver instead of the name.

---

