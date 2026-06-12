---
title: "ipod"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by shqiponj on 2006-08-18
im havin problems listening to my ipod songs. i used rythembox and gtkpod but they dont work. are there any other softwer out there.

---

### Post by %hMa@?b&lt;C on 2006-08-18
what do you mean "Don't Work"?
You should also try using amaroK.
```
sudo apt-get install amarok
```
its a KDE app, but will run on GNOME!

---

### Post by Marsolin on 2006-08-18
Here is a list of potential programs. [http://linuxappfinder.com/multimedia/portableaudiomanagers](http://linuxappfinder.com/multimedia/portableaudiomanagers)

In addition to the ones you already tried, and amaroK, which was already mentioned, there are Banshee and iPod Slave that are in the Ubuntu repositories. Banshee is a complete music player and iPod Slave is a kio-slave. A kio-slave can be used in KDE to access an iPod directly from the File Manager (or any other program) by using the link ipod:/. There is also GNUpod, but it is a commandline program.

YamiPod and myPod are two other graphical programs, but they do not have deb files so they will be more difficult to install.

---

