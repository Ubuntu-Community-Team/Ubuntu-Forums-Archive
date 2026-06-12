---
title: "LTSP client installation ended abnormally EdgyEft"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by sindile on 2006-12-29
Help and thanks in advance

Filed a bug on Launchpad bug #77324

Installed Ubuntu EdgyEft using alternate CD (have a gnome desktop)
NIC has static address 192.168.0.1 (255.255.255.0)
sudo apt-get install ltsp-server-standalone
sudo mount /dev/cdrom /media/cdrom (mount the alternate CD)
sudo ltsp-build-client --mirror file:///cdrom

Issues:
1. failure in locale setting
2. couldn't find package ltspfsd - not on CD, how can I add an argument on sudo ltsp-build-client --mirror file:///cdrom {get ltspfsd from repository}

Output of error from terminal
I: Configuring ubuntu-minimal...
I: Base system installed successfully.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /sbin/start-stop-daemon to /sbin/start-stop-daemon.real by ltsp-client'
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /etc/mtab to /etc/mtab.real by ltsp-client'
`/opt/ltsp/i386/etc/apt/sources.list' -> `/opt/ltsp/i386/etc/apt/sources.list.old'
Get:1 file: edgy Release.gpg [189B]
Get:2 file: edgy Release [1874B]
Ign file: edgy/main Packages
Ign file: edgy/restricted Packages
Fetched 2063B in 5s (345B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
laptop-detect is already the newest version.
E: Couldn't find package ltspfsd
error: LTSP client installation ended abnormally

---

