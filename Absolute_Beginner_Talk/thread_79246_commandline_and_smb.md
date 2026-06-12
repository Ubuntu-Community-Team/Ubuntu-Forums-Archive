---
title: "commandline and smb"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by Cyrus on 2005-10-19
How can I access a certain ip-address in my network with the help of the terminal?

Using the File Browser I have no problems accessing smb://192.168.1.129/Import - just how can I change my directory to that address?

I am also interested how I can copy files to that address.

cd and cp didn't work with that address ...

---

### Post by amohanty on 2005-10-19
you will need to mount the remote drive via smbfs. I cant recall offhand how to do that, but the forums are peppered with instructions as to how to do that. 

To be able to copy files to the drive, it has to be file system for which support exists in Linux.

HTH
AM

---

### Post by cwaldbieser on 2005-10-20
[QUOTE=Cyrus]How can I access a certain ip-address in my network with the help of the terminal?

Using the File Browser I have no problems accessing smb://192.168.1.129/Import - just how can I change my directory to that address?

I am also interested how I can copy files to that address.

cd and cp didn't work with that address ...[/QUOTE]
You can use a program like smbclient.  It is part of samba, I think.

---

### Post by Jussi Kukkonen on 2005-10-20
[QUOTE=Cyrus]
I am also interested how I can copy files to that address.

cd and cp didn't work with that address ...[/QUOTE]
If samba is not a requirement, but you have a ssh server on the remote machine:
```

scp [[user@]host1:]filename1  [[user@]host2:]filename2

```
Otherwise you need to mount with smbfs or use a program like smbclient.

---

