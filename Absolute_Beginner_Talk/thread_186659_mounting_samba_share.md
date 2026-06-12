---
title: "mounting samba share"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by matt91 on 2006-06-02
Iv just installed 6.06. in 5.10 i used the instructions on [http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall) to mount a windows share. i have tried this on 6.06 and get this when i try to remount:
> 
root@ubuntu-pc2:~# mount -a
mount: wrong fs type, bad option, bad superblock on //10.0.0.12/_matt,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


does anybody know how to mount a windows share in 6.06?

---

### Post by Hanj on 2006-06-02
Did you install smbfs? It yes, what does the line in /etc/fstab look like?
Mine looks like this, and it works fine:
```

//192.168.0.3/Delat /home/hannes/Filserver smbfs rw,user,username=hannes,password=xxxxxx,uid=1000,gid=1000,umask=0 0 

```

---

### Post by matt91 on 2006-06-02
Oh must have forgot to install that. I thought it was installed becouse i could access through network servers.
Thanks for your help:-D

---

