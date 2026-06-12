---
title: "KDE does not launch programs anymore"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by use a name on 2007-08-24
Since a week ago I can't launch programs from KDE anymore. The strange thing is that my previous session is restored correctly, but that's it. When I (re)start kdeinit from a terminal (which are abundant in my sessions), I can launch one more program from the menu, but then I have to do that again (and it does work for some programs, but not all (eg. OO.o does not work)). When I do so, I get the following msgs:
```

kdeinit firefox
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/bartje/.DCOPserver_XP1800__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca

kio (KService*): WARNING: The desktop entry file FreeCol/FreeCol Website.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : FreeCol/FreeCol Website.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

```
dcopserver is running and the permissions for ~/.kde are correct.

Any ideas of what might be wrong or where to look for the source of the problems?

---

### Post by DM was on fire! on 2007-08-24
Wonder if something might've corrupted in KDE.
The only thing I can think of is to back up your stuff and reinstall Kubuntu. You might also be able to install Gnome onto Kubuntu.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
Only reversed.

---

### Post by use a name on 2007-08-24
Hi, thanks for the reply.

I'd like to fix it rather than reinstalling the system. I'm affraid I might run into the same problem some other time, so I'd like to learn the cure for it. ;) I have gnome installed, so I can use that for any necessary stuff in the mean time.

---

### Post by wedge2k on 2007-10-10
I have a similar problem in gutsy,  KDED keeps crashing. and i can't find anything in the logs.

---

