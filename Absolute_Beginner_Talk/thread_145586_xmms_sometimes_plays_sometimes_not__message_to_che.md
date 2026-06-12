---
title: "xmms sometimes plays sometimes not / message to check soundcard configuration"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by dougg on 2006-03-16
Hi,
    Sometimes when I boot up then log in, XMMS works great; other times I get a message about needing to check the configuration of my sound card (something I have no idea how to do).  I know my soundcard is "on-board"; that's about it.
    Thanks for your helps.

---

### Post by Xian on 2006-03-16
[QUOTE=dougg]Hi,
Sometimes when I boot up then log in, XMMS works great; other times I get a message about needing to check the configuration of my sound card (something I have no idea how to do).  [/QUOTE]

That message is generally caused because the output plugin selection in XMMS is not compatible with the envrionment it is operating within. Open XMMS and right-click on the window, then goto Option > Preferences > Audio I/O Plugins. Change the output plugin to something like eSound or Alsa and see if it makes a difference. If not, or the problem gets worse then it most likely is just a sound conflict with some other application that is running.

---

### Post by dougg on 2006-03-17
Hmmmm.  I would be willing to use a different music player.  Which one would be a better choice for this environment?
Thanks.

---

### Post by chimera on 2006-03-17
Rythmbox. I'm having the same problem with xmms, but rythmbox always seems to work:mrgreen:

---

### Post by dougg on 2006-03-17
When I go through the initial process of loading the music library into Rhythmbox it always returns a message to to me that it does not recognize any of my audio files as audio files and then things come to a halt pretty quickly.

---

### Post by chimera on 2006-03-17
strange, that never happened to me :confused:

---

### Post by Jimmey on 2006-03-17
A temporary fix for the XMMS situation is to, before running XMMS, press the button combination ALT + F2, and then type

```
killall esd
```

Note that this will kill the system sounds ( From the menus, and shut downs, etc. )

---

