---
title: "MySQL Package Install Error"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ehanes75 on 2008-02-16
Hi,

I havebeen trying to get GPSdrive to work (which depends on MYSQL). I have run into this error when I try to install MySQL from Synaptic:

"E: mysql-server-5.0: subprocess post-installation script returned error exit status 1"

I am running Gutsy Gibbon.

Gene:](*,)

---

### Post by FakeOutdoorsman on 2008-02-16
What happens if you try to install just "mysql-server"?  It's a "metapackage" which contains mysql-server-5.0 and will probably resolve dependencies better:

```
sudo aptitude install mysql-server
```

---

