---
title: "help with uninstalling"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-28
I just installed linux dc++ using info found here:  [http://www.ubuntuforums.org/showthread.php?t=42084](http://www.ubuntuforums.org/showthread.php?t=42084)

It turns out that my college campus blocks access and now I would like to uninstall it.  How can this be done?

---

### Post by xmastree on 2005-08-28
If you installed it like this:
```
sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
```Then
```
dpkg --help
```will tell you that
```
sudo dpkg -r dcpp_0.0.20050809cvs-1~mird_i386.deb
```Will remove it.
Notice the -i (install) has changed to -r (remove)

```
man dpkg
``` for more info.

---

