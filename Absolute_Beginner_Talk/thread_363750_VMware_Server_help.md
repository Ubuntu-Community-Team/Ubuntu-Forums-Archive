---
title: "VMware Server help"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Drillbit on 2007-02-17
I recently tried to uninstall VMware Server - and now trying to reinstall -  but I keep getting this message:

paul@paul-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.plA previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.


Any ideas?

---

### Post by pebo on 2007-02-17
```
sudo rm -r /etc/vmware 
```
and try again - hth

---

