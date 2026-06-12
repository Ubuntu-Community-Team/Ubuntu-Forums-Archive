---
title: "iSCSI Target (Gutsy / AMD64 7.10 Stable)"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by MaTrIx-X on 2007-10-20
Has anyone managed to successfully set up iSCSI Enterprise Target (or any other iSCSI target) on Gutsy 64-bit?
```
matrix@ubuntu-server:~$ sudo apt-get install iscsitarget
[sudo] password for matrix:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  iscsitarget: Depends: iscsitarget-module but it is not installable
E: Broken packages
matrix@ubuntu-server:~$ 
```

I am very new to Linux, so I have not yet attempted to build this from source yet. Any suggestions would be greatly appreciated.

See also:
[https://bugs.launchpad.net/ubuntu/+bug/137096](https://bugs.launchpad.net/ubuntu/+bug/137096)
[https://bugs.launchpad.net/ubuntu/+source/iscsitarget/0.4.15-2](https://bugs.launchpad.net/ubuntu/+source/iscsitarget/0.4.15-2)
[https://launchpad.net/ubuntu/gutsy/amd64/iscsitarget/0.4.15-2](https://launchpad.net/ubuntu/gutsy/amd64/iscsitarget/0.4.15-2)

---

### Post by MaTrIx-X on 2007-10-20
Bump :guitar:

---

### Post by MaTrIx-X on 2007-10-22
Still trying to resolve this issue. Haven't found ***any*** working iSCSI target solution for Ubuntu 7.10. Any recommendation whatsoever would be a great deal of help.

---

### Post by realvz on 2007-10-22
[https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/137320](https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/137320)

---

