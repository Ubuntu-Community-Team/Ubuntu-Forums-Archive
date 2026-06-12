---
title: "trobule downloading updates"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by TheLions on 2007-11-17
when i try to get new updates i get this message:

W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/swat_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/swat_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden


W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden


W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden


W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden


W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden


W: Preuzimanje [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb) nije uspjelo
  403 Forbidden



i have ubuntu 7.10
amd 64 3800+ x2 
7600gt
2 gb ram
unlimited internet connection over LAN

---

### Post by taurus on 2007-11-17
I thought the problem has already fixed since this morning.  Try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by skyjacker on 2007-11-17
Read this thread for an explanation of what happened.      [http://ubuntuforums.org/showthread.php?t=615039](http://ubuntuforums.org/showthread.php?t=615039)

---

### Post by TheLions on 2007-11-17
> **taurus said:**
> I thought the problem has already fixed since this morning.  Try

```
sudo apt-get update
sudo apt-get upgrade
```

thanks!
that solved the problem!

---

