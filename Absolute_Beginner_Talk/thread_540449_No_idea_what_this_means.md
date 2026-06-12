---
title: "No idea what this means ??"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by traveler-1 on 2007-09-01
redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet

Can anyone explain this error ?

---

### Post by Bachstelze on 2007-09-01
Pretty self-explanatory, isn't it ? Try this

```
sudo dpkg --configure clvm
```

---

### Post by traveler-1 on 2007-09-01
Well Now I get this. Is       it   time  for a reinstall ?


Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm

If I knew what I was doing yes. 

Thanks.

> **HymnToLife said:**
> Pretty self-explanatory, isn't it ? Try this

```
sudo dpkg --configure clvm
```

---

