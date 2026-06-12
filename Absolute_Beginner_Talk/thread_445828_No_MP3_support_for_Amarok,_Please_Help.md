---
title: "No MP3 support for Amarok, Please Help"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-05-16
I installed KDE-CORE on Ubuntu.
Installed Amarok.

I had downloaded and installed gstreamer files in Ubuntu.

Mp3 playback is ok in KDE desktop on Rhythmbox and Totem, but Amarok says no Mp3 support.

What do I do ?

---

### Post by Steve H on 2007-05-16
Try [_this _]("http://ubuntuforums.org/showthread.php?t=413626")thread, I had same problem and it worked a treat for me.

Hope that helps.

:)

---

### Post by cojoco on 2007-05-24
I have had plenty of problems installing MP3 support for Amarok, and I finally believe I've found what's
causing the problems.

If you run Amarok immediately after installing it, you probably still have the Synaptic Package Manager
running, which locks /var/lib/dpkg/ and prevents any packages getting installed!

The solution that worked for me then is to:

1. Quit Synaptic
2. Quit Amarok (make sure you have quit it, not just minimized it)
3. In a terminal, 

cd /usr/lib/amarok
./install-mp3

This should eventually re-open the package manager and the installation should complete.
You may not need to go to the shell Window: with Synaptic not running, Amarok might be able
to install MP3 support by itself.

---

### Post by Xvani on 2007-05-24
> **cojoco said:**
> I have had plenty of problems installing MP3 support for Amarok, and I finally believe I've found what's
causing the problems. [...]

Did you report this? :)

---

### Post by cojoco on 2007-05-24
I'm pretty new to Ubuntu; where's the best place to report this?

Ta!

---

### Post by Xvani on 2007-05-24
i'm pretty new myself. Is this an Ubuntu or KDE bug? Amarok is a KDE app, but synaptics is where the bug probably is, so I'd go with ubuntu.

KDE:
[http://bugs.kde.org/](http://bugs.kde.org/)
to report to ubuntu:
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Not sure if the ubuntu link is the best place though...

---

### Post by Erdem on 2007-05-25
> **cojoco said:**
> I have had plenty of problems installing MP3 support for Amarok, and I finally believe I've found what's
causing the problems.

If you run Amarok immediately after installing it, you probably still have the Synaptic Package Manager
running, which locks /var/lib/dpkg/ and prevents any packages getting installed!

The solution that worked for me then is to:

1. Quit Synaptic
2. Quit Amarok (make sure you have quit it, not just minimized it)
3. In a terminal, 

cd /usr/lib/amarok
./install-mp3

This should eventually re-open the package manager and the installation should complete.
You may not need to go to the shell Window: with Synaptic not running, Amarok might be able
to install MP3 support by itself.

Thank you so much... its working well for me :)

---

### Post by nothumphrey on 2007-06-01
cheers, installing now :)

---

