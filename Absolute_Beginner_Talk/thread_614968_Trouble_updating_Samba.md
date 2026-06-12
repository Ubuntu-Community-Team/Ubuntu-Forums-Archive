---
title: "Trouble updating Samba"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-11-16
Update Mangaer shows that there are updates to Samba available, but when I try to install them, I get the following error:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb
  403 Forbidden
```


Any ideas? Thanks.

---

### Post by overdrank on 2007-11-16
[http://ubuntuforums.org/showthread.php?t=614906](http://ubuntuforums.org/showthread.php?t=614906)

---

### Post by emcconne on 2007-11-16
Same trouble here:  403 Forbidden

---

### Post by rainwalker on 2007-11-16
Same here.

---

### Post by Takster on 2007-11-16
Also here.
Check this out: [http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by Inxsible on 2007-11-16
There is a security bug in some samba packages and therefore have been disabled from download in the update manager.

it will be fixed soon enough

---

### Post by nikoPSK on 2007-11-16
I get it too, what is samba...?:p

---

### Post by Inxsible on 2007-11-16
> **nikoPSK said:**
> I get it too, what is samba...?:psamba is used to network windows machines in a share.

there is a bug with those packages and so those packages have been disabled from the download.

give it time. it will be updated with newer packages and you should be ok

---

### Post by nikoPSK on 2007-11-16
okay, cool thanks for the info...:D

---

### Post by Inxsible on 2007-11-16
> **nikoPSK said:**
> okay, cool thanks for the info...:D
No problem :)

---

### Post by nikoPSK on 2007-11-16
question: does remote desktop in gutsy work right off the bat? Mine didn't I was trying to help my friend but it gets an error...

---

