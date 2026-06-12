---
title: "Dark Screen with Quicksilver G4"
date: 2008-03-04
forum: Apple PPC Users
---

### Post by JFASI on 2008-03-04
I've been having trouble installing 7.10 on a few macs recently due to problems with liveCD's, so I've been trying to install via the alternate disks. However, one I install from an old-timey ASCII screen, the system loads fine, but the screen goes black after the Ubuntu splash screen. 

This seems to be a common issue since I can't get it to work properly on either of my G4s. The one I'm working on now is:

966Mhz PPC G4
1GB RAM
64Mb NVidia Graphics card   <- This one may need to be re-checked, but I don't want to reinstall osx to do it
Lots and lots of hard disk space. 

This will be a development and security issue machine, where I will be investigating buffer overflows and other such nasty security issues, so I will be wrecking it frequently, but I want one of the hard drives to be good copy from which I can safely restore. 

Any help would be appreciated.

---

### Post by stream303 on 2008-03-04
When it goes black, it doesn't drop you into a busybox shell prompt?

If not, I'm wondering if it is just a misconfiguration of the /etc/X11/xorg.conf file.

Can you run from a virtual terminal (ie ctrl-alt-f2)
```

dpkg-reconfigure xserver-xorg
```

If that isn't working I'd have to search for more custom G4 AGP xorg.conf files.  I'll see if I can dig anything up.

Great for finding your hardware specs:
[http://www.everymac.com/](http://www.everymac.com/)

These are handy to have:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

In the meantime, have you tried loading Feisty 7.04?  We might be able to either upgrade from there, or snag some info from it..

---

