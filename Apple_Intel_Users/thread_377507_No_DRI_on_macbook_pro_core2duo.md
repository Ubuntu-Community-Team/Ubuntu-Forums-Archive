---
title: "No DRI on macbook pro core2duo"
date: 2007-03-06
forum: Apple Intel Users
---

### Post by dionysian_mind on 2007-03-06
I have installed Edgy onto my macbook pro core2duo and followed [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") to install my ati drivers. I am running into the problem of not having DRI. My fglrxinfo output just looks like this:
```

macbook-pro:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

Does anybody have any idea what could be the problem?

---

### Post by ronocdh on 2007-03-31
Problem is probably that although the drivers are installed, you haven't "set" or "activated" them. Try running ```
sudo dpkg-reconfig xserver-xorg
``` and then making sure all your settings are correct. For instance, you may still have "Vesa" or something set as drivers on the first screen. Try manually setting this to "ATI."

Good luck!

---

