---
title: "Conflicting packages (possibly documentation mistake)"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-10
Yesterday, I wanted to install some multimedia codecs. I followed the steps I found here:

[http://help.ubuntu.com/starterguide/C/ch03.html#codecs](http://help.ubuntu.com/starterguide/C/ch03.html#codecs)

and when I tried to install the last one (universe > totem-xine), a message saying that totem-xine is conflicting with totem-gstreamer appeared.

Shouldn't the documentation state that one should remove totem-gstreamer before installing totem-xine?

And what should I do in this situation? Will my movies play without totem-xine?

---

### Post by mstlyevil on 2006-04-10
[QUOTE=zugu]Yesterday, I wanted to install some multimedia codecs. I followed the steps I found here:

[http://help.ubuntu.com/starterguide/C/ch03.html#codecs](http://help.ubuntu.com/starterguide/C/ch03.html#codecs)

and when I tried to install the last one (universe > totem-xine), a message saying that totem-xine is conflicting with totem-gstreamer appeared.

Shouldn't the documentation state that one should remove totem-gstreamer before installing totem-xine?

And what should I do in this situation? Will my movies play without totem-xine?[/QUOTE]

Usually apt-get uninstalls Totem-gstreamer for you. Totem-Xine is much better for playing movies in. Go ahead and uninstall Totem-gstreamer and all will be good.

---

