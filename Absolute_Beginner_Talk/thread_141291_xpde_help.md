---
title: "xpde help"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-03-08
I downloaded xpde .tar.gz from xpde.com and performed the following steps

1. Decompress the tar.gz in /usr/share as root
2. Edit the .xinitrc file of the user you want to run XPde and put this line:

```
/usr/share/xpde/bin/startxpde
```

3. startx

but for the third step i got this error
```

sriram@Home:~$ startx
xauth:  creating new authority file /home/sriram/.serverauth.7414
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
sriram@Home:~$
```

I also tried to run with sudo and gotr this
```

sriram@Home:~$ sudo startx
xauth:  creating new authority file /home/sriram/.serverauth.7507

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.X.Org
 for help.

sriram@Home:~$ 
```

Can anybody make out the error
thnx in advance

---

### Post by swamytk on 2006-03-08
as root stop the gdm (#/etc/init.d/gdm stop) and then try startx as normal user. It should work. It works. But, better you follow this link. Integrate xpde with GDM as instructed by this link:
[http://www.gnulinux.de/modules.php?name=News&file=article&sid=175](http://www.gnulinux.de/modules.php?name=News&file=article&sid=175)

---

### Post by daredevil on 2006-03-08
Unfortunately that article is in Dutch or French or something which is unreadable for me.... and bcos of that i also could not follow the commands given there

---

