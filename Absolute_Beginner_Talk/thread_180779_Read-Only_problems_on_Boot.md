---
title: "Read-Only problems on Boot"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by razorbuzz on 2006-05-22
Trying to boot Dapper Flight 7 (upgraded from Breezy).
I've been running with no problems for a little over a week, doing regular apt-get update/upgrades. Today, the power went out at somepoint and now when booting it tries to load but stops. Here is what the screen says:

* INIT: cannot execute "/etc/init.d/rcS"
* INIT: Entering runlevel: 2
* Loading ACPI modules... [ok]
* Starting ACPI Services...
acpid: can't open socket /var/run/acpid.socket: Read-only file system
* Starting system log...


It sits there for a while but then that fails, and then everything else fails while loading also. 
I can get to a recovery CL and I've tried remounting with "mount /dev/hda1 / -o rw,remount", but to no avail. I've followed the advice in [this thread](http://ubuntuforums.org/showthread.php?t=149064&highlight=%2Fetc%2Finit.d%2FrcS), but I don't know precisely what I am supposed to be copying over. should I copy rcS from the liveCD? Something else?
Hopefully someone has some advice to help. I've searched these forums, google, and some newsgroups...nada.

I appreciate any and all help!
Thanks.

EDIT:
Ok..I got past that issue. Now when it's trying to check all file systems It's giving errors as follows: (not verbatim, scrolls too fast after a brief pause)
/boot: clean 39/48192 files, 36896/96358 blocks (check in 3 mounts)
and does the same for /dev/hdb1 and /var.
/etc/rcS.d/S35mountall.sh is having trouble   Everything beyond there scrolls too fast for me to grab anything useful to share.

---

### Post by Sef on 2006-05-22
> Ok..I got past that issue.

How did you get past that issue?

---

### Post by razorbuzz on 2006-05-22
[QUOTE=Sef]How did you get past that issue?[/QUOTE]

I ran the same command to remount the filesystem so I could write to it.
/etc/init.d/rcS was missing, so I created it with the following contents:
```
#! /bin/sh
exec /etc/init.d/rc S
```

Thanks to a recommendation from 'ferro' in #ubuntu

---

