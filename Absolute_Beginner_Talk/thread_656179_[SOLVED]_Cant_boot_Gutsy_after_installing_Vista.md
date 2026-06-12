---
title: "[SOLVED] Cant boot Gutsy after installing Vista"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by mdewet on 2008-01-02
I have Gutsy on one partiotion, but had to install Vista for my work.  After installing Vista, the boot manager (not GRUB anymore) dont give me an option to boot Gutsty.  Only Vista is recognized.  How can I fix this to make Gutsy the default OS?  Can I reinstall Grub without reinstalling Gutsy?

---

### Post by lvleph on 2008-01-02
You can use supergrub cd to reinstall GRUB. Most likely Vista wrote over the MBR and now you are booting to the Vista Boot manager (can't remember what it is called since it is not boot.ini anymore).

---

### Post by philinux on 2008-01-02
This should help,

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jken146 on 2008-01-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

