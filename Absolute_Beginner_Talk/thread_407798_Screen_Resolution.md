---
title: "Screen Resolution"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by tombacker on 2007-04-12
I have a dual boot portable (Dell Latitude D410) with Ubuntu MS XP.  Suddenly I find that Ubuntu starts with a very low screen resolution, much lower than my preferred one of 1024 by 768.  I cannot change the resolution with the corresponding menu item, and yes, I have the root password.

So, how do one increase the resolution and make it stick?  Edit some configuration file?

Tom

---

### Post by jem7v on 2007-04-12
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) talks about fixing resolution issues.

---

### Post by kevintough on 2007-04-12
Hi Tom,

try this

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

The complete article is at

[www.help.ubuntu.com/community/FixVideoResolutionHowto](www.help.ubuntu.com/community/FixVideoResolutionHowto)

help.ubuntu.com/community/FixVideoResolutionHowto?....

Namaste,

Kevin Tough

---

