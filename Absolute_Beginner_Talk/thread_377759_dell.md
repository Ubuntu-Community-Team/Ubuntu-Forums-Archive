---
title: "dell"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Laptop1 on 2007-03-06
Hi i have a dell insprion 6400, and i dont know where to get a driver for my WLAN card its built in.

---

### Post by Bachstelze on 2007-03-06
We need to know the model of your card. Open a terminal, type *lspci* and paste what you get.

---

### Post by Laptop1 on 2007-03-06
> **HymnToLife said:**
> We need to know the model of your card. Open a terminal, type *lspci* and paste what you get.
i have a dell wireless 1390 WLAN mini-card, im in windows because i have no internet access in ubuntu.

---

### Post by melancholeric on 2007-03-06
[http://ubuntuforums.org/showthread.php?t=225706](http://ubuntuforums.org/showthread.php?t=225706)


[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by Laptop1 on 2007-03-06
> **melancholeric said:**
> [http://ubuntuforums.org/showthread.php?t=225706](http://ubuntuforums.org/showthread.php?t=225706)


[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
i have no way of downloading because i have no internet connection in ubuntu, could i download in windows and put it on a usb drive then put it on ubuntu?

---

### Post by melancholeric on 2007-03-06
Yeah. You'll need the .deb files for the build-essential package and the kernel headers. Put them to a usb stick. Then, install them with dpkg -i packagename.deb. Then you need ndiswrapper tarball ( [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz) )
Now, if I only knew what exactly the build-essential package contains. Someone else can probably help here.

There is an easier solution though.

1. Get a hammer.
2. Apply to the broadcomm wifi with sufficient force.
3. Buy an intel wifi.

---

### Post by Laptop1 on 2007-03-06
> **melancholeric said:**
> Yeah. You'll need the .deb files for the build-essential package and the kernel headers. Put them to a usb stick. Then, install them with dpkg -i packagename.deb. Then you need ndiswrapper tarball ( [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz) )
Now, if I only knew what exactly the build-essential package contains. Someone else can probably help here.

There is an easier solution though.

1. Get a hammer.
2. Apply to the broadcomm wifi with sufficient force.
3. Buy an intel wifi.
ok first off i have no idea what u said

---

### Post by Bachstelze on 2007-03-06
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here's everything you need :)

---

