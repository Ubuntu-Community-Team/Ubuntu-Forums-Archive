---
title: "Samba deamon confusion"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by ras on 2006-02-06
I've been trying unsuccessfully for some time to share a printer from ubuntu to XP.  I think its something wrong with a deamon.  I can't get XP to "see" my ubuntu home directories or printers, yet I can read & write on windows share from ubuntu.  Please help!

```
austin@mightywhitey:~$ /etc/init.d/samba restart
 * Stopping Samba daemons... start-stop-daemon: warning: failed to kill 7408: Operation not permitted
start-stop-daemon: warning: failed to kill 7411: Operation not permitted
                                                               [ ok ]
 * Starting Samba daemons.. /etc/init.d/samba: line 24:  8940 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D
                                                               [fail]
```

/etc/samba/smb.conf:
[HTML][global]
workgroup = AVHOME
netbios name = mightywhitey
printing = CUPS
printcap name = CUPS
map to guest = Bad User
show add printer wizard = No
wins support = yes
security = user
username map = /etc/samba/smbusers
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd


[printers]
comment = Print Temporary Spool Configuration
path = /var/spool/cups
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = yes

[homes]
comment = Home Directories
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700[/HTML]

Can someone explain what is happening, and what I should try?  Thanks.

-ras

---

### Post by ras on 2006-02-06
bump

---

### Post by BenTyreman on 2006-02-07
Have you tried running
```
**sudo** /etc/init.d/samba restart
```

The conf *could* be correct, but it's not loading it as the daemon restart is failing.

---

