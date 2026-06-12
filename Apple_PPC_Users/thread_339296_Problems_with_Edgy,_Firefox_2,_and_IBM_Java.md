---
title: "Problems with Edgy, Firefox 2, and IBM Java"
date: 2007-01-15
forum: Apple PPC Users
---

### Post by RedRedKrovy on 2007-01-15
I have installed IBM Java J2SE 5.0 on my system and I can't get the Mozilla Plugin working.  I have tried linking the libjavaplugin_oji.so file in ~/.mozilla/plugins, /usr/lib/mozilla/plugins, /usr/lib/firefox/plugins, and /usr/lib/mozilla-firefox/plugins.  All the Totem plugins in those directories work just fine but by god I'm pulling my hair out trying to get the Java plugin to work.  What am I missing?  It has to be something simple.  Any ideals?

By the way I just updated to Edgy by doing a clean sweep and starting over from scratch.  Everything I've done worked just fine in Dapper.

---

### Post by badgerclan on 2007-01-16
No problem installing Java on my Mini. Just followed the directions at: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
for the PPC:)

---

### Post by RedRedKrovy on 2007-01-16
Problem solved, I didn't have libgtk1.2 installed.  Funny how the test applet worked but the firefox plugin didn't until that was installed.

---

