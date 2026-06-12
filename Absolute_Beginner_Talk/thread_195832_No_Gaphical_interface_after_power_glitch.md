---
title: "No Gaphical interface after power glitch"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-06-13
I was upgrading to 6.02LTS and encountered a power glitch. Upon rebooting the install was unable to recover and to make matters worse my graphical interface , X server is now out of wack. Can I recover from this?

The only clues I can offer are 
(==) Log file: "/var/log/Xorg.0.log"
(==) Using config file "/etc/X11/xor.conf"

First I had selected and installed Samba then I had tried to upgrade to Ubuntu 6.01 LTS. The plan is to use the Linux machine as a file server for 2 Windows machines.

When I have more time I plan to come back to Ubuntu and move away from Windows.

---

### Post by daller on 2006-06-17
You should finish your upgrade first...

Then run:

```
sudo dpkg-reconfigure xserver-xorg
```

It'll reconfigure your entire (almost) Xorg setup!

Please reply if you stumple during the setup!

---

