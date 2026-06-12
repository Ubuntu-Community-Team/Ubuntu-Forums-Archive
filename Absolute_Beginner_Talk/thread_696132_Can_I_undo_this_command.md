---
title: "Can I undo this command?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by mezcla on 2008-02-13
I wanted to install Amarok 1.4.8 and thought I had to compile it since it wasn't in Synaptic.  At the request of the how-to I was using I ran:

```
sudo apt-get build-dep amarok
```

which installed a lot of KDE things.  Today I found out that I could enable gutsy backports and install amarok through Synaptic.  I just want to remove this and the amarok installation before I proceed.  I am running gutsy 64-bit and need this version of amarok to work with my ipod nano 3rd gen.  Thanks in advance for any assistance.

---

### Post by Blutack on 2008-02-13
This might help, be very careful.
[https://answers.launchpad.net/apt/+question/8366](https://answers.launchpad.net/apt/+question/8366)
You may be much safer having a look in /var/log/dpkg.log, finding all the packages that you install with the build-dep and then manually removing them.

---

