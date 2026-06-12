---
title: "Mounting samba shares with write, files r read only?!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by mortuk on 2007-05-25
Hey all, managed to get samba shares with write access working using the credentials method in the /etc/fstab

```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777
```

Anyways it works, but whenever I copy a file into the directory it has read only on so I cant edit it, any ideas?

Cheers

---

### Post by REDISISTone.nl on 2007-05-25
I suppose you try to connect to A Windows PC ? In that case you need NTFS support (just look on the forum or on doc.gwos.org)

Otherwise, If you are trying to connect to another Ubuntu (or linux) based computer, you have to play with the rights (and again, find it on the forum or doc.gwos.org or the manual of samba/ubuntu)

Good luck!!

---

### Post by Najand on 2007-05-25
You should configure your samba configurations: Samba's configuration is stored in the smb.conf file, which usually resides in /etc/samba/smb.conf or /usr/local/samba/lib/smb.conf.
And change the readonly part to "read only = no"

---

