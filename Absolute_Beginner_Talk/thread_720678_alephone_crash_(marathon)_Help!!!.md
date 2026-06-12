---
title: "alephone crash (marathon)??? Help!!!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by pugofdestiny on 2008-03-10
Hi maybe im on a 64bit computer (ubuntu gutsy 7.10) i installed marathon (alephone) from 
[http://source.bungie.org/](http://source.bungie.org/) and it worked fine for awile but recently its been crashing whenever i try to play single player or join a multiplayer game it changes my screen and makes my screen giant sized and then gives me the following error can you help me ive already tried recompiling the source code
heres the error.


X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x1a5
  Serial number of failed request:  184
  Current serial number in output stream:  186

any ideas?

---

### Post by Het Irv on 2008-03-10
I looks like the program is not playing nice with your XServer, since you said that the program was working for a while I would suggest resetting your XServer configuations to the default settings.
```
sudo dpkg-reconfigure xserver-xorg
```
**WARNING: This will clear out all of you configurations, If you have made any changes take notes on them.**
If your not sure about a setting use the default.  If you have made changes I would suggest doing them one at a time and trying the program after each change to make sure that they don't affect the program.

---

### Post by pugofdestiny on 2008-03-10
thnx but i figured it out it was sumtin even wierdier i had the game set to full screen in fullscreen mode but then i made in small screen in full screen mode and it worked thnx though

---

### Post by Het Irv on 2008-03-11
Wow, thats...umm...okay, whatever works.  Let one of the Devs of that game know what you did to fix the problem, it may be a bug they don't know about.

---

