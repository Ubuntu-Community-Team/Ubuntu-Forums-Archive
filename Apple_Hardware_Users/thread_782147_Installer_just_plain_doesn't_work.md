---
title: "Installer just plain doesn't work"
date: 2008-05-04
forum: Apple Hardware Users
---

### Post by Termagant on 2008-05-04
I'm on an iBook G4 (PowerPC) running Mac OS X 10.4.

When I boot from the CD, I get the first screen. So I type "live". (I've also tried "live-powerpc" with the same result.)

It shows a black text-on-white screen, which goes by too quickly for me to read, then shows this error message twice:

Cannot allocate resource region 0 of device

Then it shuts down.

Any ideas? Thanks in advance

---

### Post by frog_pilot on 2008-05-05
Which ubuntu version are you trying?

The white screen with black text is normal. It shows video hardware detection details.

For different boot-options look here [PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues").

If you only want to install, I suggest to take the alternate cd. It comes with a non gui installer.

On my ibook G4 the standard ppc hardy live CD is working fine in default boot (type nothing on the first boot screen).

And there comes up two times this error message:
```
Cannot allocate resource region 0 of device xxxxxxxx
```
But then startup will continue.

---

