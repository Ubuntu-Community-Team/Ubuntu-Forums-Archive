---
title: "Opera amd64 on i386"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Ubuntutard on 2006-02-10
Hi
I know there are other threads about this, but I didnt understand anything as I started to use Ubuntu 5.10 today. My problem is i really want opera as my webbrowser. and this happens: 
sudo dpkg -i --force-architecture opera-static_8.51-20051114.1-qt_en_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package opera-static.
(Reading database ... 78193 files and directories currently installed.)
Unpacking opera-static (from opera-static_8.51-20051114.1-qt_en_i386.deb) ...
dpkg: dependency problems prevent configuration of opera-static:
 opera-static depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera-static (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera-static

What does this mean? I dont understand any of this. Any help would be very much appreciated :)

---

