---
title: "my monitor went blank"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-07-21
after reading this thread [http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647) i changed my 915resolution
and the effect was that my screen went blank after i login and password. though the system is still running as i can hear the startup music. 
i want to undo what i did in the 915resolution
any help

---

### Post by ddrichardson on 2007-07-21
<CTRL><ALT>Numeric + will go up resolutions and - down them.

Use <CTRL><ALT><F2> to give you a virtual terminal and then alter the /etc/X11/xorg,conf file to change the resolution back.

<CTRL><ALT><Backspace> will kill the x server allowing you to restart it after you've configured.

---

### Post by annda on 2007-07-21
if you haven't backed your xorg.conf, boot into recovery mode and run this:

```
dpkg-reconfigure -phigh xserver-xorg
```

this should help. in the future, always back up xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then you can restore it with this command:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by rahul_bhise on 2007-07-23
tanks for the help
first i did   <CTRL><ALT>Numeric +
then    sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
then    sudo apt-get install xserver-xorg-video-intel
and uninstall 915resolution by synaptic
now everything is going right

---

