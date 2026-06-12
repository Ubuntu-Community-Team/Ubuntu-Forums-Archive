---
title: "Update problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by weverjames on 2007-11-16
Hello.
Today I tried to update my system as usual, but something was not as usual.  It did not completed.  This was what it showed:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden

Does anyone know what happens?

Hello everyone I have came back:KS

---

### Post by PriceChild on 2007-11-16
A defect has been identified in a recent security update and as a result the associated packages have been taken offline. Please disregard any 403 errors you may receive when trying to apply updates. They will disappear once this problem is resolved.

---

### Post by taurus on 2007-11-16
[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

---

### Post by carlosjuero on 2007-11-16
> **PriceChild said:**
> A defect has been identified in a recent security update and as a result the associated packages have been taken offline. Please disregard any 403 errors you may receive when trying to apply updates. They will disappear once this problem is resolved.
Hrm - does this mean that I will be getting a rollback update/patch? I downloaded all of the recent updates on my desktop and server with no issues today (earlier in the AM). What sort of defects are we talking about here?

---

