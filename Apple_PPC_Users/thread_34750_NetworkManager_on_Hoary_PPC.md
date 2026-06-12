---
title: "NetworkManager on Hoary PPC"
date: 2005-05-16
forum: Apple PPC Users
---

### Post by hupf on 2005-05-16
Hi folks!

I try to build NetworkManager on Hoary PPC. I exactly did it as described in [this thread](http://www.ubuntuforums.org/showthread.php?t=11150), but I always get the following error:

```
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x65c): In function `nmwa_update_state':
/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:290: undefined reference to `_'
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x774):/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:327: undefined reference to `_'
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x80c):/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:300: undefined reference to `_'
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x834):/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:315: undefined reference to `_'
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x8c8):/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:324: undefined reference to `_'
./.libs/libnm_notification_applet.a(NMWirelessApplet.o)(.text+0x13d4):/home/m/network-manager-0.3.1+cvs20041101/panel-applet/NMWirelessApplet.c:657: more undefined references to `_' follow
collect2: ld returned 1 exit status
make[3]: *** [NetworkManagerNotification] Error 1
make[3]: Leaving directory `/home/m/network-manager-0.3.1+cvs20041101/panel-applet'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/m/network-manager-0.3.1+cvs20041101/panel-applet'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/m/network-manager-0.3.1+cvs20041101'
make: *** [install-arch] Error 2
Build command ‘cd network-manager-0.3.1+cvs20041101 && dpkg-buildpackage -b -uc’ failed.
E: Child process failed
```

Has somebody occurred the same error?

Greetings,
hupf

---

