---
title: "Ubuntu takes about 5 minutes to log on.."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-05-14
after I type my U/N and P/W It takes about 5 minutes until my desktop comes up and when it does i get this error:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Whats it mean and does anyone know how to fix it.

Note: Not an error in terminal. Its a popup dialog box.

---

### Post by caffienefree on 2007-05-15
Switch to a terminal from gnome (Press Ctrl+Alt+F1) and type the following.


mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/

Now restart, and see if it helps?

---

