---
title: "Samba install symlinks problems"
date: 2006-11-25
forum: Apple PPC Users
---

### Post by Lars Noodén on 2006-11-25
The basic installation of the samba package seems to have some problems making symlinks.  Here is a short way to get the error once it's installed:

[INDENT]sudo dpkg-reconfigure samba[/INDENT]
[INDENT]invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
[/INDENT]

Uname says:
[INDENT] Linux desktop 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux[/INDENT]

and /etc/lsb-release says:
[INDENT] DISTRIB_ID=Ubuntu[/INDENT]
[INDENT] DISTRIB_RELEASE=6.06[/INDENT]
[INDENT] DISTRIB_CODENAME=dapper[/INDENT]
[INDENT] DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"[/INDENT]

---

### Post by Lars Noodén on 2006-11-25
Here is the error that is shown when ```
apt-get install
``` is used:

```
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
```

---

