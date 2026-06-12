---
title: "WLAN Problems (linux-wlan-ng)"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by jak-_- on 2005-09-09
I tried to follow the How-To at [http://ubuntuforums.org/showthread.php?t=25676&highlight=prism2_usb](http://ubuntuforums.org/showthread.php?t=25676&highlight=prism2_usb)

The problem is, when I do "sudo apt-get install linux-wlan-ng" as how-to told me, it just tells me "E: Couldn't find package linux-wlan-ng".


Tried searching (cd and hd), Tried synaptic, Tried downloading linux-wlan-ng myself (failed, obviously) and now I'm out of ideas, (as the only thing I actually managed to do was install latest nvidia drivers)



Atm, the WLAN works, but very unreliable, and very slow, thought I should try and get some proper drivers on.



 - Jak-_- | thanks in advance.

---

### Post by Steve1961 on 2005-09-09
Have you made sure the universe and multiverse repositories are enabled in synaptic.

---

### Post by jak-_- on 2005-09-09
[QUOTE=Steve1961]Have you made sure the universe and multiverse repositories are enabled in synaptic.[/QUOTE]

No idea what they are, but I've enabled them anyway :)

I tryed searching with them on, and it just got linux-wlan-ng-doc, but not the actual thing.

---

### Post by Steve1961 on 2005-09-09
The repositories are servers containing software that can be installed on synaptic.  Not sure why the driver doesn't appear - I've tried as well and I can't find it either.  That said, I'm using the AMD 64 version and not all the software is available for this.  One final suggestion, if you haven't done so already, add the backports repositories as described in this guide, and search again:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Anybody else got any ideas?

---

### Post by jak-_- on 2005-09-09
[QUOTE=Steve1961]That said, I'm using the AMD 64 version and not all the software is available for this.[/QUOTE]


Oh, that could be it :|...

Is it possible to install the x86 version on a 64bit chip? (ie, like you do with windows 32bit on 64bit chips...)

---

### Post by Steve1961 on 2005-09-09
Yes, no problem at all.  I started with the 32bit version and changed to 64bit when I received the disc.  Can't say I notice much of a difference.

---

### Post by jak-_- on 2005-09-09
[QUOTE=Steve1961]Yes, no problem at all.  I started with the 32bit version and changed to 64bit when I received the disc.  Can't say I notice much of a difference.[/QUOTE]


```
meez@haven:~$ sudo apt-get install linux-wlan-ng
Reading package lists... Done
Building dependency tree... Done
Package linux-wlan-ng is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-wlan-ng has no installation candidate

```

:\... Looks like I'm gonna be leeching the x86 install tonight ^^.

---

### Post by poofyhairguy on 2005-09-09
[QUOTE=jak-_-]Oh, that could be it :|...

Is it possible to install the x86 version on a 64bit chip? (ie, like you do with windows 32bit on 64bit chips...)[/QUOTE]

Yes...in fact its recommended by us on the forum.

---

