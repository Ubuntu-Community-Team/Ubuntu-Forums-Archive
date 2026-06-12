---
title: "[SOLVED] samba, smb install forbidden"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-11-16
I tried to download these critical updates but was told it was forbidden. Any thoughts?

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

---

### Post by pdlethbridge on 2007-11-16
my bad! a server change from us to main solved the problem.

---

### Post by Boondock5 on 2007-11-16
How do I change the server? I'm having the same issue.

---

### Post by venkaya on 2007-11-16
I still have the same problem.... I cant update 4 items... libsmbclient, libsmbclient -dev, samba-common...



get error 403 forbidden

thanks if u can help me out...

---

### Post by quibbler on 2007-11-16
System - Administration - Software Sources

Ubuntu Software - Download from ...change this to Main server

---

### Post by venkaya on 2007-11-16
I already change the server to main but sitll have the same problem:



W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb](http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb)
403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb](http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb)
403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb](http://security.ubuntu.com/ubuntu/po...tu2.1_i386.deb)
403 Forbidden
__________________

---

### Post by HippoMan on 2007-11-16
> **quibbler said:**
> System - Administration - Software Sources

Ubuntu Software - Download from ...change this to Main serverCould someone also explain how to make this change manually in **/etc/apt/sources.list?**  I don't use any of the gui-based package managers.

Thanks.
[RIGHT].
[/RIGHT]

---

### Post by HippoMan on 2007-11-16
> **HippoMan said:**
> Could someone also explain how to make this change manually in **/etc/apt/sources.list?**  I don't use any of the gui-based package managers.Well, I finally figured it out via trial-and-error.  Make the following changes in **/etc/apt/sources.list**:

All occurrences of **us.archive.ubuntu.com** => **main.archive.ubuntu.com**
All occurrences of **security.ubuntu.com** => **main.archive.ubuntu.com**

Then, do a **sudo apt-get install**.
[RIGHT].
[/RIGHT]

---

### Post by nikolai on 2007-11-16
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

The updates were disabled in purpose because it creates a vulnerability described in the above thread.  Just wait until it's fixed to update samba.

---

