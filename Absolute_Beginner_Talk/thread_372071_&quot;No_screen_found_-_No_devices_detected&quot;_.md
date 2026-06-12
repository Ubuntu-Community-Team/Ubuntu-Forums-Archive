---
title: "&quot;No screen found - No devices detected&quot; I screwed up XD Help me revive my Ubuntu!!"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Fireblend on 2007-02-27
So, I was trying to install beryl this morning and I guess that caused this, since I installed a driver I thought my graphics card supported and apparently... it doesn't. So, now the graphic interface won't load. As the error said, I went to wiki.x.org and it said:

> If you are using a distribution you should rerun its configuration tool. If there is no such tool, or if it keeps configuring your Xserver wrong you may want to try xorgcfg, the graphical tool shipped with Xorg. You can also let the server generate a config file: as root just run X -configure.

So:
How do I run this configuration tool? I can enter the recovery mode fine, so I guess there's a command to get it running there?
If not, how do I run this xorgcfg?
If not, how do I generate this config file/login as root?

Thanks in advance!

---

### Post by Brunellus on 2007-02-27
log in to the console.

then

sudo dpkg-reconfigure xserver-xorg

and follow the prompts.

Next time you hack up xorg.conf, remember to keep a backup of the last working configuration.

---

### Post by Maestro23 on 2007-02-27
> sudo dpkg-reconfigure xserver-xorg

After you get the system back up, you can re-install the driver for your card.

*And stay away from Beryl.:)

---

### Post by Fireblend on 2007-02-27
Thanks for the help! I'll try this right now. And yeah, I won't be playing around with Beryl until it get stable :p Definitely learned my lesson there.

---

