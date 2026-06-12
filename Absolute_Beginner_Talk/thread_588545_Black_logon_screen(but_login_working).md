---
title: "Black logon screen(but login working)"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by dhearth on 2007-10-23
I installed the video drivers which were recomended in the restricted driver(or something like that) program in the system menu on the top taskbar. For my radeon x1550 series, 512mb.

 When I restarted the pc due to instructions telling me to, I can see the splash screen and boot up, but the logon screen is black with no mouse or anything. However I know I can logon because if I type my logon details in I can hear the startup and login sounds.

Going to ctrl+alt+f1 and doing "sudo dpkg -reconfigure xserver-xorg" makes it, at first say something about warranty, then the rest of the time offer help with the dpkg command.

---

### Post by Qwerty_ on 2007-10-24
The correct command is

```
sudo dpkg-reconfigure xserver-xorg
```

no space between dpkg and -reconfigure.

---

### Post by Riggs on 2007-12-26
I have the same problem, except I just installed 7.10, 32bit edition.  I never had this problem before I installed my other XFX 7600GT.  Does Ubuntu have issues with SLI?  I've read some people are having no luck with the dpkg-reconfigure command.  I can see the Ubuntu logo during boot, then hits the login screen and get the Ubuntu login screen sound.  I can even log in (even though I can't see what I'm typing) and I hear the statup sounds and I can see the hard drive light going on.  Any suggestions on what to do here?

---

### Post by Riggs on 2007-12-27
bump

---

