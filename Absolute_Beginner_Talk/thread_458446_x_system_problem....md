---
title: "x system problem..."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ouch67 on 2007-05-29
well I thought I'd try ubuntu today so I downloaded it and burned it to a cd. when rebooting to try the live boot thing I got some errors that say the x_system couldn't start. reading the logs it says that screens were found but that they could not be configured.

anyone come across this before?

I'm running a 2.5ghz celeron with around 500MB of ram free and a radeon 7000 card. not sure if it uses the hard drive as cache or something but I have 45gb free on that.

The computer is a compaq presario, s4100nx but the hardware has been modified as above.

---

### Post by ggaaron on 2007-05-29
You can run
```
sudo dpkg-reconfigure xserver-xorg
```
from a normal console and configure xserver, its quite common error, it means that ubuntu failed to set up X automatically - search the forums for xorg configuration or something.

---

