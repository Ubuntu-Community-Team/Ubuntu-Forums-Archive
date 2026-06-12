---
title: "Forcing Ubuntu to *not* connect to a particular wireless network"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by luvinthegibbon on 2007-12-03
Cos I run a server at home, I used my ubuntu7.10 laptop to temporarily connected to my neighbour's wireless net to check external access to my site.  The problem is that I don't want to connect to that network any more, but my laptop insists on connecting to it at boot-up.

Also, after a while of using my home wireless connection, my laptop decides to disconnect, and start using my neighbours connection again.

Can anyone advise how to tell Ubuntu to *stop* using a particular connection?

---

### Post by x64Jimbo on 2007-12-03
You can try using my script for this...
[http://ubuntuforums.org/showthread.php?t=385051](http://ubuntuforums.org/showthread.php?t=385051)

---

### Post by Bigbird999 on 2007-12-03
If you install wicd (search the networking forum) it replaces network manager and it shows you all of the available networks and allows you to select  one (yours presumably) to automatically connect.

For this newb it works far better than network manager

BB

---

### Post by luvinthegibbon on 2007-12-04
Thanks guys.

**x64Jimbo**: I had a look at your script, and it looks like it removes entries from the gconf config.  Since I've only connected to a couple of networks, it was easy enough for me to remove them by hand with gconf-editor.

So, this should stop my laptop stealing my neighbour's connection?

---

