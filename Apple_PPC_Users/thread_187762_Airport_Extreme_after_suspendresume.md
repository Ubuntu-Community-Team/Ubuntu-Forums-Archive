---
title: "Airport Extreme after suspend/resume"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by sulobanks on 2006-06-03
I saw this on the development forum before the official release of Dapper and there wasn't a solution yet.  The problem is that when you suspend, then resume, the wireless connection doesn't come back up.  No amount of dhclient, networking restart or unloading/realoading the bcm43xx driver will do any good. All it does is attempt to get an ip address from the access point (which it apparently sees) and times out.  Anyone have any suggestions?  It really defeats the purpose of suspend for me if upon resuming I find that I have to reboot completely in order to get my network connection back.

---

### Post by goofyheadedpunk on 2006-06-03
[QUOTE=sulobanks]I saw this on the development forum before the official release of Dapper and there wasn't a solution yet.  The problem is that when you suspend, then resume, the wireless connection doesn't come back up.  No amount of dhclient, networking restart or unloading/realoading the bcm43xx driver will do any good. All it does is attempt to get an ip address from the access point (which it apparently sees) and times out.  Anyone have any suggestions?  It really defeats the purpose of suspend for me if upon resuming I find that I have to reboot completely in order to get my network connection back.[/QUOTE]

My hackish fix was to add the appropriate wireless access point and key to /etc/network/interfaces then, upon waking the laptop, issue `sudo /etc/init.d/networking restart'. Worked mostly.

---

### Post by bluemonki on 2006-06-12
So does this:

```
#sudo modprobe -r bcm43xx

then

#sudo modprobe bcm43xx
```

Not work?  It's a bit of a hack but it saves a reboot...

---

### Post by Tatey on 2006-06-12
I use just reload the module and it works again. Slightly annoying, but I can tolerate it.

---

