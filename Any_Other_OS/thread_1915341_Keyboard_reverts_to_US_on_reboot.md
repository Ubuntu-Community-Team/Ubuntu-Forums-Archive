---
title: "Keyboard reverts to US on reboot"
date: 2012-01-26
forum: Any Other OS
---

### Post by sunfromhere on 2012-01-26
Keyboard reverts to US layout on every reboot.

I've had this issue on Ubuntu, Debian, Fedora and it was easily fixed - while on log-in screen I selected the layout I wanted and it stopped reverting.

But... CentOS log-in screen has no keyboard options, only language.

Googling gives me only the solution I knew already, and which doesn't work here. Any ideas?

EDIT: editing /etc/sysconfig/keyboard doesn't work

EDIT2: found a "solution" - KDE. Installed KDE for testing purposes, changed keyboard layout, didn't revert on reboot. Perhaps it's a gnome bug?

---

### Post by sunfromhere on 2012-01-26
I am marking this thread as unsolved.

I just installed OpenSUSE, same issue.
Log-in window has no keyboard options, and the keyboard layout reverts to US on every reboot/relog.

This is the fifth Linux distro that I have seen exhibiting the same issue.
Why does this happen?

---

### Post by mips on 2012-01-26
See,

[http://ubuntuforums.org/showthread.php?t=1568439](http://ubuntuforums.org/showthread.php?t=1568439) (Maybe post#7 ?)
[http://ubuntuforums.org/showthread.php?t=1414858](http://ubuntuforums.org/showthread.php?t=1414858)
[http://ubuntuforums.org/showpost.php?p=10668853&postcount=2](http://ubuntuforums.org/showpost.php?p=10668853&postcount=2)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530999](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530999)
[https://bugs.launchpad.net/indicator-applet/+bug/688936](https://bugs.launchpad.net/indicator-applet/+bug/688936)

---

