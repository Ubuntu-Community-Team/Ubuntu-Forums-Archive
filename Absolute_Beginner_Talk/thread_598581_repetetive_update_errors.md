---
title: "repetetive update errors"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by kigango123 on 2007-10-31
i have been trying to update but i keep getting these errors


> Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/Release.gpg](http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/Release.gpg)  Could not connect to mirror.randumb.org:80 (69.42.222.102), connection timed out
Failed to fetch [http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/multimedia-experimental/i18n/Translation-en_US.bz2](http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/multimedia-experimental/i18n/Translation-en_US.bz2)  Could not connect to mirror.randumb.org:80 (69.42.222.102), connection timed out
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/source/Sources.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/source/Sources.gz)  Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/binary-i386/Packages.gz](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Failed to fetch [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/source/Sources.gz](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz)  404 Not Found

it cant be because of the keys, can it, i just spent like two days scouring the net for gpg key files that i installed and now this
Are the sources wrong or what is it i am doing wrong

---

### Post by taurus on 2007-10-31
You can either edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out those repos by placing a # in front of them or post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by kigango123 on 2007-10-31
it worked!, i am finally good. all i have to do now is to go 7.10

---

