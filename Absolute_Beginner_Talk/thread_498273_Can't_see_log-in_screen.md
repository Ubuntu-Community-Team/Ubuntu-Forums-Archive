---
title: "Can't see log-in screen"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by grayarea on 2007-07-11
I am a new Ubuntu user. Installed on an old PIII 800Mhz PC and old parts I had lying around. It was all working fine including wireless internet, wireless printing etc. I was very impressed. However I changed a simple thing ... the monitor ( a old CRT for a slightly less old LCD) and now I can't see the log-in screen as the monitor does not support the video mode. However I log-in blind as any user and then everything works fine. I suspect that it is the refresh rate specified on the log-in screen. As various users the screen works fine if I am at 60 Hz or 72 Hz.

Therefore my question is how can I change the screen resolution and refresh rate just for the log-in screen?

Many thanks

---

### Post by bernied on 2007-07-11
You can try:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
sudo dpkg-reconfigure xorg-xserver
```
The first line makes a backup of your current configuration (restore to the backup by reversing the file names in the command).
The second line re-runs the utility that configures video hardware during the install process.

You will then have a bunch of questions to answer.

---

