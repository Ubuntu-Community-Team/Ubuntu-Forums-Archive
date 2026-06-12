---
title: "[SOLVED] smbclient"
date: 2008-06-08
forum: Arch and derivatives
---

### Post by Dr Small on 2008-06-08
Can I use smbclient without installing samba? I really don't want to bother with setting up Samba (since no one really connects to my computer anyhow...) and I only want to connect out to my Mom's computer (Windows...) to transfer some of the pictures from the camera.

I installed smbclient, but I really don't know how to use it, and I am constantly getting this error when using it:
```
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
	No such file or directory
smbclient: Can't load /etc/samba/smb.conf - run testparm to debug it

```

So.. back to my original question. Can I use smbclient without having Samba installed?

Dr Small

---

### Post by Tenken on 2008-06-08
You don't need the samba service to use smbclient, according to [this]("http://bugs.archlinux.org/task/3743") a blank smb.conf file should fix the problem.

---

### Post by Dr Small on 2008-06-09
Ok, thanks. Generally I don't think **bug** because I am sure it is something I have done :D That did the trick though, and I found some documentation on using smbclient, so everything is good now. Thanks.

Dr Small

---

