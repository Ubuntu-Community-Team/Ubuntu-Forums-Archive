---
title: "Unable to start mpd under Intrepid on MBP(3,1)"
date: 2008-11-12
forum: Apple Hardware Users
---

### Post by hellmitre on 2008-11-12
Denizens of the Ubuntu Fora, I come to you with a plea. I am having issues getting mpd to run. It's installed on my system, but when I initially used sudo apt-get install mpd to install it, I got an error with dpkg, which looked like this:
```
Setting up mpd (0.13.2-2ubuntu1) ...
 * Starting Music Player Daemon mpd                                              * creating ~/.mpd/mpd.db... 
Segmentation fault
                                                                         [fail]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's installed now, as I can run mpd --create-db and watch it spit out a nice output of my ~/Music folder's contents. When I try running mpd by itself, I get a segmentation fault. What's giving?

---

### Post by cyberdork33 on 2008-11-12
check for / file bugs in Launchpad.
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

