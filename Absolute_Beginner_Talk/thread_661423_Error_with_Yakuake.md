---
title: "Error with Yakuake"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-01-07
I installed and tried to run yakuake but this is the error that I received:

Error: Can not create link from "/home/noorez/.kde/socket-noorez-laptop" to "/tmp/ksocket-noorez"
Error: Can not create link from "/home/noorez/.kde/socket-noorez-laptop" to "/tmp/ksocket-noorezUHSeX3"
trying to create local folder /home/noorez/.kde/socket-noorez-laptop: Permission denied
trying to create local folder /home/noorez/.kde/socket-noorez-laptop: Permission denied
kdeinit: Aborting. bind() failed: : No such file or directory
Could not bind to socket '/home/noorez/.kde/socket-noorez-laptop/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.

Can someone help with this?

---

### Post by Xavieran on 2008-01-07
Yakuake was made for use in KDE and you are using GNOME...

KDE has it's own set of software libraries and GNOME has to have special plugins to be able to use KDE apps...

I would suggest using Tilda,which is the GNOME alternative and (in my opinion) much better...

code:
```
sudo apt-get install tilda
```

---

