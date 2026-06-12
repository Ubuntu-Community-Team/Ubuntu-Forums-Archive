---
title: "update manager"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by hawthorne90250 on 2007-11-10
Hi
  After trying to install a .deb file for my printer, the update manager now says

Could not initialize the package information
A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:The package hl1270nlpr needs to be reinstalled, but I can't find an archive for it.'

 I downloaded the file again and when i try to install it using package installer
"this package may be corrupted or you are not allowed to open the file.check permission of the file".


luke@luke-laptop:~$ sudo dpkg -i hl1270nlpr-1.1.2-1.i386.deb
dpkg: error processing hl1270nlpr-1.1.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
I am using Ubuntu 7.10.
                                            Thanks

---

### Post by taurus on 2007-11-10
Are you in the right directory when you try to install it?  Perhaps you downloaded it to ~/Desktop.

```
cd ~/Desktop
sudo dpkg -i hl1270nlpr-1.1.2-1.i386.deb
```

---

### Post by hawthorne90250 on 2007-11-10
Yes it was the wrong directory, i corrected this and tried to install, it still does not seem to install.
luke@luke-laptop:~/Desktop$ sudo dpkg -i hl1270nlpr-1.1.2-1.i386.deb
(Reading database ... 90109 files and directories currently installed.)
Preparing to replace hl1270nlpr 1.1.2-1 (using hl1270nlpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1270nlpr ...
/var/lib/dpkg/info/hl1270nlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1270nlpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1270nlpr-1.1.2-1.i386.deb
                                                 Thanks

---

