---
title: "qt libraries and headers"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by bump_ on 2007-08-23
Hi,

I'm not sure if this is the right place for kubuntu questions, but it's pretty generic I think. I am trying to install a theme manager from source. SO i uncompressed it easily enough, so i move on to ./configure. It seemed to be going ok when this popped up
```
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```

So i did
```
apt-cache search qtlib
``` 

and installed

```
libqt4-core-kdecopy - Qt 4 core non-GUI functionality runtime library
libqt4-dev-kdecopy - Qt 4 development files
libqt4-gui-kdecopy - Qt 4 core GUI functionality runtime library
libqt4-qt3support-kdecopy - Qt 3 compatibility library for Qt 4

```
because they looked the most likely.

I tried it again and I still got the same problem. I noticed in my apt-cache search, nothing pertaining to headers came up. Could this be the problem?

---

### Post by Blutack on 2007-08-23
sudo aptitude install libqt3-headers
You might need some more kde headers though.

---

### Post by bump_ on 2007-08-23
I tried what you said, but it never finished installing. Every time I try, my computer restarts at
```
Updating fontconfig cache...
```

Then when it restarts, it tells me to run
```
dpkg --configure -a
```
since it got inturrupted and I do, but it just restarts again.

so I tried
```
dpkg --purge -a
```
and tried strating the install again, but it just restarts at that line

ANy help?

---

