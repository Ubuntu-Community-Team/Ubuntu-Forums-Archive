---
title: "ubuntu studio install problem -solved"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by _user1_ on 2007-08-07
After installing ubuntu studio it would boot up to the point of logging in (it played the login sound) but the screen was black.  I could boot with the rescue option and get a command line, but being a newbie that wasn't much help.  So I took the easiest route for me and maybe it will help someone else.

  I had left my Ubuntu v7.04 on the original partition and had installed Studio in it's own partition.  That meant I could boot my regular version and replace the incorrect Studio's xorg.config with the one from my install of Ubuntu v7.04, which I knew to be correct.  The file I copied was:  /etc/x11/xorg.conf).  

It worked for me.

---

