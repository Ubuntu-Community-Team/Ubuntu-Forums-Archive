---
title: "Update Manager always fails to download xserver-xorg-core"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by brucewagner on 2008-01-19
I am a brand new user of Ubuntu 7.10 64-bit.

Update Manager is always trying to update xserver-xorg-core

And it fails every time, giving this message...


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  404 Not Found


What should I do?

---

### Post by sloggerkhan on 2008-01-19
This keeps happening to me, too.

---

### Post by Udaho on 2008-01-19
There was a problem with the last xorg update that went out and it ended up crashing a lot of java applications. I believe what is happening to you guys (and happened on my laptop) is that the offending update has been removed from that repository. It's not a bad thing you can't download it, it's preventing you from downloading something that could mess up some of your applications.

[http://ubuntuforums.org/showthread.php?t=672004](http://ubuntuforums.org/showthread.php?t=672004)

---

### Post by astoltz on 2008-01-19
As Udaho said, the problem with the original upgrade package caused the Devs to pull it from the repos.  It's since been fixed but the package is at a new version number.  You just need to reload the package info:  Open a terminal and put in: ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by michaelzap on 2008-01-19
Or just click on the Check button in the Update Manager and it will automatically find the new version which you will be able to download.

---

### Post by sloggerkhan on 2008-01-19
I think for me it's just that cs.utah.... hosted mirror is down.

---

### Post by RomeReactor on 2008-01-19
> **sloggerkhan said:**
> I think for me it's just that cs.utah.... hosted mirror is down.

Hi. The package is now xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3; download either of these and double-click to install:

* [32-bit package]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb")
* [64-bit package]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_amd64.deb")

---

### Post by sloggerkhan on 2008-01-20
My update manager went okay when I switched to using the generic US mirror and refreshed. So okay now.

---

