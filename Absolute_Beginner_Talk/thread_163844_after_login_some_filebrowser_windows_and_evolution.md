---
title: "after login some filebrowser windows and evolution open"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by byenary on 2006-04-21
Hello, 

been using ubuntu for a while now, got this strange thing going on now, when i login in i get a couple file browser windows and my evolution already open, it looks like he is restoring a position where i was at some point ? something like hibernate does.
When i close all windows, log of, and than login everything is open again....
Breezy ghosts eh

---

### Post by louis_nichols on 2006-04-21
no! it's just a session thing. just click logout and on the screen with options (logout, reboot etc.) you have a checkbox called "save current session". just check that and next time your desktop will only show windows that were open at logout.

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=byenary]Hello, 

been using ubuntu for a while now, got this strange thing going on now, when i login in i get a couple file browser windows and my evolution already open, it looks like he is restoring a position where i was at some point ? something like hibernate does.
When i close all windows, log of, and than login everything is open again....
Breezy ghosts eh[/QUOTE]
Go under System > Preferences > Session and make sure that "Automatically save changes to session" is not checked. If that doesn't work make sure that it is not a startup program (Click the Startup Programs Tab and make sure that it is not there).

---

### Post by louis_nichols on 2006-04-21
[QUOTE=MasterChief1234]Go under System > Preferences > Session and make sure that "Automatically save changes to session" is not checked. If that doesn't work make sure that it is not a startup program (Click the Startup Programs Tab and make sure that it is not there).[/QUOTE]

actually, checking the option is what he needs. only then will his session react to him closing windows that he doesn't want open at login. otherwise, it will just open the session that was last saved, which obviously contained those apps.

---

### Post by byenary on 2006-04-21
Thx cheking the option did the job

---

