---
title: "MythTV install via Synaptic (not a good idea?)"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-08-10
After visiting the MythTV website, I started installing it myself, but, when I saw all the dependencies, I thought, why not check out Synaptic? It found it and installed it.

However, after it was finished, there was no MythTV in the menus, so I tried opening it from the command line. This was the result:

```
2005-08-10 21:24:37.612 Switching to square mode ()
2005-08-10 21:24:37.622 Unable to connect to database!
2005-08-10 21:24:37.622 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-08-10 21:24:37.629 Switching to square mode (blue)
Segmentation fault

```
Would it be better to install via apt-get? Is there a way to fix the current installation?

Any help would be greatly appreciated.

---

### Post by KingBahamut on 2005-08-10
Try here

[http://www.mythtv.org/docs/mythtv-HOWTO-21.html](http://www.mythtv.org/docs/mythtv-HOWTO-21.html)

---

### Post by mikeb on 2005-08-11
[QUOTE=KingBahamut]Try here

[http://www.mythtv.org/docs/mythtv-HOWTO-21.html](http://www.mythtv.org/docs/mythtv-HOWTO-21.html)[/QUOTE]
 Many thanks, KingBahamut. I see what I'll be doing most of today ;-)

---

### Post by KingBahamut on 2005-08-11
Sure sure mike, no problem. 

When you get it running, cross post back on what you did and so forth. 

Kinda helps the others get the gist.

---

