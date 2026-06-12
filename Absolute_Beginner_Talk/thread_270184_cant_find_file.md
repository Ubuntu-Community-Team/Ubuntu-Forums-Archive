---
title: "cant find file"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by stealth75711 on 2006-10-02
i installed breezy badger when i run apt-get update i get
this message:Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch/main Packages
  Unable to fetch file, server said 'Can't open /debian-marillat/dists/etch/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Fetched 4B in 2s (1B/s)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/etch/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Reading package lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_etch_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


## how do i fix my sources.list?

---

### Post by annda on 2006-10-02
read those, they are really helpful:
very practical, hands-on
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

and more details here:
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by stealth75711 on 2006-10-02
(gedit:8986): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
amin@ubuntu:~$



## Now it says this..](*,)  and it wont let me save
the sources.list!!

---

### Post by podunk on 2006-10-02
Did you maybe forget to 
sudo
?

```
gksudo gedit /etc/apt/sources.list 
```

also you will have to sudo to download any packages.

---

### Post by stealth75711 on 2006-10-02
thats thhe command i typed in to get the error message
when i type in sudo gedit i dont getr the error

---

### Post by stealth75711 on 2006-10-02
Ok thanks it finally started working
:KS

---

