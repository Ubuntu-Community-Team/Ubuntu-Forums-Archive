---
title: "External firewire CD boot made easy!"
date: 2008-02-16
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-16
All these boot problems from CD got me thinking about my external firewire cdrom/dvd drive again.  There are quite a few threads, but I did some digging and lo and behold it was very easy.

[http://ubuntuforums.org/showthread.php?t=320690&highlight=firewire+boot](http://ubuntuforums.org/showthread.php?t=320690&highlight=firewire+boot)

For me, it was as simple as booting into open-firmware by giving my iMac the 4-finger salute (command-option-O-F) while powering up then

when the openfirmware boot prompt came up

I just issued the command:
```
[B]
boot fw/node/sbp-2/disk:,\install\yaboot[/B]
```

and up came Hardy Heron alpha live from the firewire cd.  Just don't confuse CTRL with COMMAND (cloverleaf) like I do all the time.

This might be useful not only for installing Ubuntu but maybe for those who wish to install a dvd-only distribution on their older/broken cd drive boxes.

---

