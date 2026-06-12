---
title: "Easy way to install dependent packages?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Dwaylu on 2007-03-08
I'm trying to install VLC Player on Ubuntu Edgy, but whenever I run the command sudo apt-get install vlc, I get a list of dependent packages I need to download and install.

Is there can easier way to obtain all of those dependent packages other than running out and downloading and installing them separately?

---

### Post by yabbadabbadont on 2007-03-08
Apt is just telling you that it is going to download and install those extra packages *for you*.  You don't need to do it manually.

---

### Post by mikewhatever on 2007-03-08
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by Dwaylu on 2007-03-08
```
The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6a-jb-videolan-1) but it is not going to be installed
       Depends: libdbus-1-2 (>= 0.60) but it is not installable
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6a-jb-videolan) but it is not going to be installed
       Depends: libwxgtk2.6-0 (>= 2.6.1.2ubuntu2) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
E: Broken packages
```

Is that the same thing or am I missing something?

---

### Post by yabbadabbadont on 2007-03-08
Did you download a deb file from somewhere and install it instead of just using the vlc in the Edgy repositories?  When I first replied to you, I thought you were just talking about the normal output when you run "sudo apt-get install vlc"...

---

### Post by aysiu on 2007-03-08
Your repositories list is messed up.

**Step 1**: [Get a fresh list](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Install VLC: ```
sudo apt-get update && sudo apt-get install vlc
```

---

