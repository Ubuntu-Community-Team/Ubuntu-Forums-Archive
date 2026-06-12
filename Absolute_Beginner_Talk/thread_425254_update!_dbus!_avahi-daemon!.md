---
title: "update! dbus! avahi-daemon!"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by the badger on 2007-04-27
hi.

updated from dapper to edgy with hopes of moving on to feisty - i know, it's a risky move for a newbie, but i can always reinstall dapper if all else fails.
anyhow, ran 
> gksu "update-manager -c" 
and got 
> warning: could not initiate dbus
Error in sys.excepthook:
Original exception was:
ran
> sudo /etc/init.d/dbus restart
and it's telling me
>  * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 

what to do??
[i found another poster]("http://ubuntuforums.org/showthread.php?t=416520&highlight=upgrade+avahi-daemon") who had an avahi-daemon failure, and fixed it by editing /etc/network/interfaces, but i'm not sure it's the same problem - i don't know how to manipulate "interfaces" so i can edit it.

i reckon i should remedy this avahi-daemon failure/dbus prob before plowing along into feisty. but that said, i cannot do so without YOUR HELP... ?
thanks.
---------
the lure of the glowing black screen is great, but my knowledge is little...

---

### Post by zvacet on 2007-04-27
```
sudo gedit /etc/network/interfaces
```

---

