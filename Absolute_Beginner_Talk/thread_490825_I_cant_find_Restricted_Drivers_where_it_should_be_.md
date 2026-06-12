---
title: "I cant find Restricted Drivers where it should be help"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Ice Dragon on 2007-07-02
I have been trying to instal my x1100 radeon mobile driver on my laptop in ubuntu, what ive read on the internet says that I need to goto system -> administration -> restricted drivers.. however restricted drivers is just not there on my ubuntu installation for some reason.

Anyone know where it is located or why its not where it should be?

---

### Post by 3rdalbum on 2007-07-02
Restricted Drivers Manager is only in 7.04. If you are using 7.04, try going to a terminal and typing:

```
gksudo restricted-manager
```

If you are using earlier versions, go into Synaptic and look for "linux-restricted-modules" that matches your kernel version. (you can find your kernel version by typing uname -r at the command prompt).

After that, you will have to open up Xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

And change the driver name from "ati" to "fglrx". Save changes and reboot.

---

