---
title: "Communicating with Mac OSX"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Autolycus on 2008-04-13
Just installed Ubuntu 7.10 on a PC based machine (my old windows machine).  I need some help on communicating (networking) with a mac running OSX 10.4 and 10.5. Also, I have a second hard drive on the PC I'd like to use as storage. How should this be formatted inorder to be Macintosh aware?

Thanks,

ShadowSailor

---

### Post by aktiwers on 2008-04-13
I have used SSH both ways many times. Go to Places => "Connect to server.." and fill in the OSX pc info.

Maybe you need to install Ssh on osx first? I can't remember. But it works :)

---

### Post by wormser on 2008-04-13
> **aktiwers said:**
> I have used SSH both ways many times. Go to Places => "Connect to server.." and fill in the OSX pc info.

Maybe you need to install Ssh on osx first? I can't remember. But it works :)

That is probably the easiest way.  OS X already has Open SSH Server installed.  You can test it in the command line first.

```
ssh UserNameOnMac@IPaddress
```

---

