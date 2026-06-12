---
title: "security updates won't install-Gutsy"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-11-17
When I attempt to install the following ubuntu security updates, it fails and gives me these error messages:

libsmbclient
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)

  403 Forbidden


samba common
smbclient

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)

403 Forbidden

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
403 Forbidden

Does anyone know how I might get these  updates to install.
Thanks

---

### Post by philinux on 2007-11-17
If they were the last updates I just got the 5 mins ago and all installed without a hitch, I wonder if the servers overloaded, try again in ten mins.

---

### Post by Beggar on 2007-11-17
Ive been having the same issue since last night.  Something strangely humourous about 403s from the security repo.. anyways, it seems to be a problem on the main us servers, short term fix is to just change the repository you are using to the main ubuntu repo, im assuming like me you were using the us server. if not, please let me know, ill go check launchpad for the bug, and if its not there file one.

Edit: looks like someone botched the release pretty hard, [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163116](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163116)

---

### Post by wieman01 on 2007-11-17
Nothing to worry about... just wait a little while and try again. The servers are probably down.

---

### Post by Beggar on 2007-11-17
The servers are not down, its a confirmed issue...

---

