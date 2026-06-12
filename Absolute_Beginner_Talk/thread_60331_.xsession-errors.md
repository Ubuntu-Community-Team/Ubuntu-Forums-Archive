---
title: ".xsession-errors"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by Seb Spiers on 2005-08-27
Ive just installed unreal tournament 2004, but it wouldnt run, so I rebooted.  Now I have the following error when I login.
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "seb"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Trinity:
_IceTransMakeAllCOSTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by ISC connection
_IceTransOpen: transport open failed for isc/Trinity:
_IceTransMakeAllCOSTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by SCO connection
_IceTransOpen: transport open failed for sco/Trinity:
_IceTransMakeAllCOSTSServerListeners: failed to open listener for sco

** (gnome-session:7904): WARNING **: Unable to read ICE authority file: /home/seb/.ICEauthority
```
Anyone got any ideas? :)

---

### Post by chruesu on 2005-08-27
```
Unable to read ICE authority file: /home/seb/.ICEauthority
```

hi! I think I had the same problem:

try this:
```

sudo chown seb /home/seb/.ICEauthority
sudo chgrp seb  /home/seb/.ICEauthority
```

maybe also:
```
sudo chmode 755  /home/seb/.ICEauthority
```

However, kindly note the follwoing:
[list]
[*]I don't know why this error occured - however it happened already several times on my system . explantions? anybody?
[*]this is maybe rather a 'dirty' solution - if at all? better suggestions? anybody?
[/list] 

hope this was useful...
regards

---

### Post by tonysathre on 2005-08-29
sudo chmode 755  /home/seb/.ICEauthority

this should be -- sudo chmod 755  /home/seb/.ICEauthority

---

