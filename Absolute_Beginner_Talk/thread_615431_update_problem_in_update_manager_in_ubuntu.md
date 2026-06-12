---
title: "update problem in update manager in ubuntu"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-11-17
The little orange star icon popped up in my taskbar but when i try to download and install some things cant be downloaded i get this message 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


what do i do? I am running Xubuntu

---

### Post by PmDematagoda on 2007-11-17
This is nothing wrong, everyone is facing this problem. It is very likely that the Ubuntu Security Team has restricted the updates because they may be defective, the updates will be available again after they are fixed.

---

### Post by BusDriverBloke on 2007-11-17
I got the same last night and this morning It was trying to download:

libsmbclient
samba-common
smbclient

I got the following 403 error messages

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden

---

