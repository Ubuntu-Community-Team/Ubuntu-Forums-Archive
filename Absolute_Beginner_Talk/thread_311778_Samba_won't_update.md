---
title: "Samba won't update"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-12-03
I have tried to update this several times, and update manager isn't able to get thru it either. This is the error message I get in terminal when I try to aptitude update:

```
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Evidently the problem lies in my system's file configuration, but I don't have a clue as to how to fix it...

---

