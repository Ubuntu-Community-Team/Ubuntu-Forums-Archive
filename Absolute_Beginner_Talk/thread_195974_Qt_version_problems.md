---
title: "Qt version problems"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-06-13
I'm trying to compile a font manager from [here]("http://linux.softpedia.com/get/Utilities/Font-Installer-12722.shtml") but I get the following error:

```

checking for libjpeg... no
configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```

The thing is I installed qt last night from a  .tar.bz file called 
qt-x11-opensource-src-4.1.3.tar.gz which is the latest version - post qt 3.3.
Is there anyway to check that I compiled it correctly? Or the version? 
Im confused!
Whats happening??

---

### Post by hugelmopf on 2006-07-12
If you want to compile against Ubuntu's Qt version, you should use this package, which includes the Qt headers: libqt3-mt-dev

Install that and then you should be set for compiling the font manager (is the Kubuntu one in System Settings not good enough?).

---

