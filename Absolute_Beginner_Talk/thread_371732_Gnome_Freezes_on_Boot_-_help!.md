---
title: "Gnome Freezes on Boot - help!"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-27
This is the first time since Saturday morning I've had to boot into XP.  Gnome is freezing just after login.  The original tan background is all that I see and a white box up in the top left corner (about 10% of the screens length and width).  The box seems to be part of the background, or if its a window that can't load I have no control over it.  I can press ctrl+alt+f# to get into the terminal, but I'm not sure what I can do from there to help me out.

Thanks!

---

### Post by Meson on 2007-02-27
Some more info on this.

In the terminal the following message was periodically showing up:
```
[17179741.984000] bcm43xx: Error: Microcode 'bcm43xx_microcode5.fw' not available or load failed.
```

Eventually I heard the login noise (maybe after about 10 of those messages in the terminal.  So I typed exit and then ctrl+alt+f7.  The white box revealed itself to be an error message.  It was in a window with a close button but here's the text:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Most of the stuff in my administration tab is not loading.  I tried to get a list of my startup programs.  I also tried to do something with the network, but that didn't load either.

---

### Post by TimDuncan on 2007-04-23
i got this too. Only after upgrading to feisty. I found deleting .gconf from home folder fixes this, but as soon as i edit any gnome settings the problem comes back.

If anybody has any fixes or help I would greatly appreciate this too!!! thanks!

Tim

---

