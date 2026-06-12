---
title: "[SOLVED] Sound Problem after Install"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Jimhawk on 2007-08-11
I've been getting no sound at all after freshly installing 7.04. I've tried many of the posted fixes all over the forums and have gotten no results whatsoever. I'm running a Dell Dimension 4600 Desktop with an AC 97 ICH5 onboard sound chip. Does anyone have any advice for me to get my sound working?

---

### Post by moore.bryan on 2007-08-11
[I]this might be overkill for your problem, but it took all this to get my sound working on a lenovo thinkpad z61e...
grab the alsa stuff and compile from source:
[alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")
[alsa-lib-1.0.14a]("ftp://ftp.alsa-project.org/pub/driver/alsa-lib-1.0.14a.tar.bz2")
[alsa-utils-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-utils-1.0.14.tar.bz2")
[alsa-tools-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-tools-1.0.14.tar.bz2")
[alsa-firmware-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-firmware-1.0.14.tar.bz2")
[alsa-plugins-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-plugins-1.0.14.tar.bz2")
[alsa-oss-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-oss-1.0.14.tar.bz2")
[pyalsa-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/pyalsa-1.0.14.tar.bz2")
and then run ```
alsamixergui
``` to set the volumes, ```
sudo alsactl store
``` to keep your settings and add ```
alsactl restore
``` to your /etc/rc.local file.
[/I]

---

### Post by riven0 on 2007-08-11
Then after that, try resetting your sound: sudo /etc/init.d/alsa-utils reset


That's what finally worked for me.

---

