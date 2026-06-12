---
title: "Services and configuration"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by belaflek on 2007-09-11
So am I correct that the list of services is the /etc/init.d folder and the config files for said services are in the /etc/default folder? Im a Windows admin trying to get off the Microsoft teat so my technical knowledge is there..its just figuring what changes effect what.

---

### Post by chrono310 on 2007-09-11
eh... I'm not exactly sure I know what you're asking, but I'll give it a shot.

The scripts that are in /etc/init.d are generally used to start and stop services. The /etc directory holds all the configuration files. Also, settings that are user specific are generally saved in the home directories of the users (system/hidden files are preceeded with a '.'), so your gnome settings may be in the ~/.gnome directory. To see a list of processes that are running, you can run:

```
ps ax
```

You can pipe the output from that into grep to search for specific processes, like so:

```
ps ax | grep firefox
```

This will give you the process ID and some other info about the process. Hope that clears some things up.

---

