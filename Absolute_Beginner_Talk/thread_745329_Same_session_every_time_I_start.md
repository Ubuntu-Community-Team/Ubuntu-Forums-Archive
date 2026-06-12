---
title: "Same session every time I start"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by charliwest on 2008-04-04
Hello

I have a little issue here. If I shut down my pc, running Xubuntu, when I start it up again I always have the same session come up, I don't mean the last session, but one from a few weeks ago. 

I have tried shut down from the terminal, restart, suspend, and normal shut down, but always the same session. I know it sounds minor but its always got the same folder open, awn starts up again so I have a few of them running and system monitor so I have to shut them down everytime I start.

Any help would be great.

Thanks

---

### Post by banewman on 2008-04-04
Open up    system settings - sessions and startup   and select to remember sessions.
Close the apps you don't want and logout and back in - should fix the issue.
:)

---

### Post by Michael.Godawski on 2008-04-04
In the Ubuntu desktop there is a menu called Sessions

System > Preferences > Session

There must be something similar in Xubuntu. Check there if you can disable some unwanted applications.

---

### Post by sisco311 on 2008-04-04
delete the session files:
```
rm ~/.cache/sessions/*
```

---

### Post by charliwest on 2008-04-20
Thanks everyone, that last one by sisco311 worked a treat!

---

