---
title: "screwed up Xserver-xorg"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Deviltongue on 2007-03-24
I screwed up the xorg.conf trying to configure it for AIGLX I tried to use ```
sudo dpkg-reconfigure xorg.conf
``` but when I rebooted I couldn't get my old resolution instead I had 1024x768 which makes scrolling all jumpy at 61 Hrtz refresh rate! so i tried configuring the xserver but that didn't change anything!!! HELP!!!!

---

### Post by lamalex on 2007-03-24
the command is
```
dpkg-reconfigure xserver-xorg
```
try that and hopefully it will fix your problem

---

### Post by Deviltongue on 2007-03-24
I just tried it and I tried to set the resolutions I want and everything but I'm still getting the same problem

---

### Post by bulldog on 2007-03-24
Did you install drivers for your graphics?
And is your card properly listed in your xorg.conf?

---

### Post by Deviltongue on 2007-03-24
yea, it is

---

### Post by bulldog on 2007-03-24
The thing is,you should have an error message when you invoke a bad command.
I don't read anything about that.

But can you tell what kind of graphics you have,and maybe some more info about your xorg.conf,maybe even copy it here?

---

