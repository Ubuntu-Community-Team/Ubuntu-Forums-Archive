---
title: "[SOLVED] Synaptic Error MMap ran out of room:"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-09-25
Hello, i get an error when I sudo apt-get update then upgrade, and I get the same thing from my update manager.

Here is is from the update manager.

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing klipper (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
```

Now the update manager is in the notification area all the time with this error. It started after a sudo apt-get update and upgrade. 

I honestly don't need klipper I only installed KDE to change the theme of Amarok.

TIA for help, and if no help is available, then I thought I should put it out there. i assume someone will want my sources.list, but I'll wait to be sure.

---

### Post by coldstatue on 2007-09-25
BTW - 

```
sudo apt-get remove klipper
Password:
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing klipper (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

---

### Post by coldstatue on 2007-09-25
SOLVED:

Oddly, I guess it was something to do with my e17 repo. Disabled it, ran synaptic, got a bunch of KDE updates.(And recommended installs for KDE apps - 30 MB total.)  Hmph. I don't get it, but there it is for those who understand.

---

