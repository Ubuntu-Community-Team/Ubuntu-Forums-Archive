---
title: "fix desktop permissions set to root?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by thegreenman on 2007-05-06
It seems my desktop is somehow set to root permissions.  home/chris/Desktop this doesn't seem right, and now I can't delete or move anything from mys desktop. How can i fix this?

---

### Post by taurus on 2007-05-06
```
sudo chown -R chris:chris /home/chris/Desktop
ls -la ~/Desktop
```

---

### Post by thegreenman on 2007-05-06
taurus you win the award for**[COLOR="Blue"] fastest fix ever[/COLOR]**. Thanks mucho.

---

