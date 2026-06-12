---
title: "Software installs end with &quot;no space on /boot partition&quot;"
date: 2013-12-14
forum: Any Other OS
---

### Post by azzivar on 2013-12-14
I'm running Ubuntu Gnome 3 (Wheezy) and encrypted my hard drive.  When I run gparted, I'm not allowed to change the size of the /boot partition, which is the only un-encrypted partition.  I can't change the encrypted disk as it's all one large partition.

How can I resolve this issue?  I've been through the files on /boot, but I don't want to delete anything without knowing the consequences.  In retrospect, I should have made the /boot partition larger.  Is there anything I can do without starting from scratch and reinstalling the system.  This is a single OS PC.

thanks,
Greg

---

### Post by Impavidus on 2013-12-14
You probably have a bunch of old kernels. There are several threads about this. For example, you can uninstall some using this one-liner:
```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```However, you must first get your package manager into a consistent state. To do so, manually delete some big files with old version numbers from /boot and repair the package manager. I don't remember the exact command to do so, but I think apt-get will tell and there are several threads about that too.

---

### Post by oldos2er on 2013-12-14
Moved to Other OS/Distro Support.

---

