---
title: "Starting and stopping ESD the right way..."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-04-28
In order to get the sound working for UT2004 I used to use a nice little workaround that involved a "sleep 5" command in the initialization script for the file but now that I'm launching it in it's own X-session to stop it from fighting with Xgl that won't work any more.

Now I'm using "killall esd" before I run it and that works fine. However, when I come back from the game I can't figure out how to restart esd without logging out and back in.

Just typing "esd" gives me an error. I'm not at my computer right now so I can't be any more specific. Sorry.


Is there a better way to stop and restart ESD than killing the process? I've looked at the documentation but it's filled with so many options it makes my head spin. Maybe I need some more parameters when I restart it? Is there a way to find out what command the system is running when I log in to enable it?

Thanks!

---

### Post by Tangent on 2006-10-14
You can reinitiate esd by using the command
```
esd &
```

---

### Post by jordanmthomas on 2006-10-14
I have to start esd with root permissions
```
sudo esd &
```

I stop it the same way you do, but again, I have to throw sudo into it.
I love the sound it makes when it starts

---

