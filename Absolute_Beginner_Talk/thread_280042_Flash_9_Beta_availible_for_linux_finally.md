---
title: "Flash 9 Beta availible for linux finally"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by chuckyp on 2006-10-18
I'm sure most of you know but just in case here ya go flash 9 beta for linux was released today.

[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

---

### Post by jordanmthomas on 2006-10-18
I didn't know.
Installed.
Thanks.

---

### Post by WalmartSniperLX on 2006-10-18
YES! Ill install it once I get home :D

---

### Post by Apotheosis on 2006-10-18
Awesome!  Thanks for the heads-up.

---

### Post by rbmorse on 2006-10-18
And, so far it works good!

---

### Post by jordanmthomas on 2006-10-18
I can play games again!
...is this good or bad?

---

### Post by barkej on 2006-10-19
Cool. Thanks for letting me know.

---

### Post by dolphinsonar on 2006-10-19
Is there a way to sudo apt get that?

---

### Post by jordanmthomas on 2006-10-19
I'm not sure.  It's easy enough to install though.
Save the tarball to your Desktop
Open a terminal
```
cd ~/Desktop
tar xvf FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55/
sudo mv /usr/lib/firefox/plugins/libflashplayer.so  /usr/lib/firefox/plugins/libflashplayer.so.THISISTHEOLDONE
sudo cp libflashplayer.so  /usr/lib/firefox/plugins/
```

This will back up your old flash player (just in case) and put the new one in its place.

---

