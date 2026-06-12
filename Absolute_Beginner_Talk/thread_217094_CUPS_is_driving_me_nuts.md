---
title: "CUPS is driving me nuts"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by debernardis on 2006-07-16
It worked until two days ago. Then, no more.

```

$ less /var/log/cups/error_log
E [16/Jul/2006:20:44:29 +0200] Creating missing directory "/var/run/cups/certs"
E [16/Jul/2006:20:44:29 +0200] Unable to open output file "file:/dev/usblp0" - No such file or directory.

```

```

$ invoke-rc.d cupsys restart
 * Restarting Common Unix Printing System: cupsd                                                                                          
cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "restart" failed.

```

```
$ ps -aef | grep cupsd
1000      7784  6404  0 21:36 pts/2    00:00:00 grep cupsd

```

```

$ dpkg -l | grep cups
ii  bluez-cups                             2.24-0ubuntu6                         Bluetooth printer driver for CUPS
ii  cupsys                                 1.2.1-0ubuntu2                        Common UNIX Printing System(tm) - server
ii  cupsys-bsd                             1.2.1-0ubuntu2                        Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                          1.2.1-0ubuntu2                        Common UNIX Printing System(tm) - client pro
ii  cupsys-driver-gutenprint               5.0.0~rc2-0ubuntu6                    printer drivers for CUPS
ii  libcupsimage2                          1.2.1-0ubuntu2                        Common UNIX Printing System(tm) - image libs
ii  libcupsys2                             1.2.1-0ubuntu2                        Common UNIX Printing System(tm) - libs
ii  libgnomecups1.0-1                      0.2.2-1ubuntu5.1                      GNOME library for CUPS interaction

```

No thread seems to improve this situation.
Help anybody?

---

### Post by rdd on 2006-07-16
Have you tried some of the stuff in this bugreport?

[https://launchpad.net/products/cups/+bug/31339](https://launchpad.net/products/cups/+bug/31339)

Regards

rdd

---

### Post by debernardis on 2006-07-17
Done it, I had to reinstall the weird samsung installer for my sx-4100, as described in [http://www.ubuntuforums.org/showthread.php?p=1265540#post1265540](http://www.ubuntuforums.org/showthread.php?p=1265540#post1265540)

---

