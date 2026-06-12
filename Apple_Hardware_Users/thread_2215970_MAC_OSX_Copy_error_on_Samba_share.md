---
title: "MAC OSX Copy error on Samba share"
date: 2014-04-09
forum: Apple Hardware Users
---

### Post by marc19 on 2014-04-09
I've created a samba server on Ubuntu Server 13.10. I want to share an external exfat formated disk (USB3). 

The disk is mounted with: 
```
mount -t exfat -o rw,uid=1000,umask=002 /dev/sdf2 /media/share/
```

The smb.conf:

```

   path = /media/share
   browsable = yes
   create mask = 0755
   read only = no
   comment = share
   writeable = yes
   available = yes

```

When I connect my imac (iOS 10.8.5) to the SMB than I can see the share. All working, I can open folders, create folders, but when I copy a file to the share I wil get after the copying an error msg. However the file is full functional copied. I can open it and do anything with it.
For the error see the screenshot. 
[ATTACH=CONFIG]251861[/ATTACH] (in english: finder error -36)

Have anybody a solution for this issue?

Thanks a lot

---

