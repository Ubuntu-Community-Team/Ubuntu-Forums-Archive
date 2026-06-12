---
title: "how do I tell Firefox where last.fm is?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-25
When I try to open a last.fm station in firefox, it tells me that the protocol isn't associated with any program.  I looked in prefs, but couldn't find anywhere to give it new protocols.  How do I do that?  -pete

---

### Post by localzuk on 2006-02-25
There used to be a plugin which allowed you to assign applications to protocols. However, as I cannot find that one, these ones might do the trick for you.

[https://addons.mozilla.org/extensions/moreinfo.php?id=446&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=446&application=firefox)
[https://addons.mozilla.org/extensions/moreinfo.php?id=81&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=81&application=firefox)

They allow external applications to be launched for each link. Also, one allows you to replace streams embedded in pages with a link to launch an external application. Hope this helps

---

### Post by TeeAhr1 on 2006-02-25
SOLVED.  For anyone searching this, just drag the link into the last.fm player.

---

### Post by TeeAhr1 on 2006-02-26
SOLVED BETTER: From the last.fm faq...
> In Firefox, type in "about:config" in the location bar right click, select New --> String

name of string should be: "network.protocol-handler.app.lastfm"

value should be the path to your player.exe, eg "~/Last.fm/player", on a PC "C:\Program Files\Last.fm Player\player.exe"

You learn something new every night. :)

---

### Post by malmjako on 2006-03-08
[http://www.last.fm/help/faq.php#238](http://www.last.fm/help/faq.php#238) according to last.fm FAQ.

---

