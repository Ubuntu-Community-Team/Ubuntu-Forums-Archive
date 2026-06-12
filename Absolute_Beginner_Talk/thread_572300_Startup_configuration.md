---
title: "Startup configuration"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by lionround on 2007-10-10
This has probably been asked a thousand times, but I could not find the answer I need while searching.

I want to be able to start ndiswrapper and samba on startup.  I know the commands: modprobe ndiswrapper and /etc/init.d/samba start however I don't know where to put these in order to make them run at startup.

There is a folder ~/.config/autostart but there is nothing in it.

Thanks

---

### Post by nick_h on 2007-10-10
For ndiswrapper just add a line to /etc/modules

---

