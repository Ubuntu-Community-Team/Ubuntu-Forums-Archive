---
title: "pinning firefox- apt-get doesn't listen to synaptic"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-04-29
this is minor annoyance. but I figured, this might as well be a bug which might need to be fixed bf dapper comes out. I mean, I'm pretty sure I'll be pinning fx 1.5 in apper, when fx 2.0 comes out... 

here is the problem:

I have fx 1.5.0.2 thus don't need the 1.0.8 update. I pinned it (and its friend, shown below) to 1.0.7 using synaptic's packages>lock version, but when I do apt-get upgrade, it still wants to upgrade firefox. synaptic is just fine, it doesn't prompt me to update fx. here is the output for your viewing pleasure:
```

:~$ sudo apt-get **-s** upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  firefox firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst **firefox-gnome-support** [1.0.7-0ubuntu20] (1.0.8-0ubuntu5.10 Ubuntu:5.10/breezy-security) []
Inst **firefox** [1.0.7-0ubuntu20] (1.0.8-0ubuntu5.10 Ubuntu:5.10/breezy-security)
Conf firefox (1.0.8-0ubuntu5.10 Ubuntu:5.10/breezy-security)
Conf firefox-gnome-support (1.0.8-0ubuntu5.10 Ubuntu:5.10/breezy-security)

```both of these are supposed to be pinned by synaptic... 

Should I:
1. file a bug bc this is ubuntu's fault?
or
2. stop being annoyed bc this is my fault?

---

### Post by aysiu on 2006-04-29
File a bug report.

---

### Post by towsonu2003 on 2006-04-29
[QUOTE=aysiu]File a bug report.[/QUOTE]
I'll obey :mrgreen:

---

### Post by towsonu2003 on 2006-04-29
and here it is:
[https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/42178](https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/42178)

---

