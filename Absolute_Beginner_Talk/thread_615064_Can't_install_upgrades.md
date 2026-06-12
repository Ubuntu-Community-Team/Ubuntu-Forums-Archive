---
title: "Can't install upgrades"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-11-16
Getting this error

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


What do I do?

---

### Post by shad0w_walker on 2007-11-16
It's a temporary issue. They are fixing a bug with the packages and have prevented them from being downloaded until it is fixed. Just wait for the moment and it will be sorted.

---

### Post by phoenix23 on 2007-11-16
Any news on this? It's still not working for me.

---

### Post by jbguev on 2007-11-16
I am having the same problem with 3 updates: samba-common, smbclient, and libsmbclient.

Jerry

---

### Post by FuturePilot on 2007-11-16
There's a problem with the update package. It's flawed. So they blocked it from being downloaded. Best to just wait it out. You can read more on this here
[http://ubuntuforums.org/showthread.php?t=463944]("http://ubuntuforums.org/showthread.php?t=463944")

---

### Post by phoenix23 on 2007-11-17
I was able to fix this by doing 

sudo apt-get update

in terminal.

---

### Post by por100pre1 on 2007-11-17
> **phoenix23 said:**
> I was able to fix this by doing 

sudo apt-get update

in terminal.

That issue has been solved.

---

