---
title: "/etc/init.d scripts don't restore on package reinstall"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by mystrim on 2006-05-12
Hello,

I inadvertantly deleted the file /etc/init.d/courier-imap-ssl.  One would think this wouldn't be a huge problem - simply reinstall the courier-imap-ssl package, and the script should reappear.  Indeed, a package repository search for the file shows that it is in that package, not some other generic package for init.d scripts.  However, reinstalling the package does not put the file back in place.  I cannot find this file anywhere on the net.  Just for kicks, I deleted a few other scripts from /etc/init.d and tried reinstalling the packages.  The files don't reappear for any package in Ubuntu where they are supposed to (and possibly all flavors of Debian).

Can someone help me out?  Could I at least have a copy of the files I need (/etc/courier-*)?  Is this a known bug, or am I the first to report it?

Thanks,

Tim

---

### Post by cyracks on 2006-05-12
```
ar x package.deb
```

will extract package

Maybe if you completely remove the package, it would set all files back in second install.

Synaptic: mark for complete removal
```
sudo apt-get remove --purge package.deb
```

---

