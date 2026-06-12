---
title: "Both Panels Gone"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by MMalen on 2007-07-17
I accidentally double clicked on my bottom panel and now both panels have disappeared and I don't know how to get them to come back.  I can still alt+tab between programs in the workspace that I'm in but I can't switch workspaces or access either panel.  Help!

--Massey--

---

### Post by sancho panza on 2007-07-17
See if [this helps]("https://help.ubuntu.com/7.04/user-guide/C/gospanel-5.html").

---

### Post by MMalen on 2007-07-17
Not really, because I don't have a "hide button" anywhere so there's no button to un-hide it.  Thanks anyway,

---

### Post by MMalen on 2007-07-17
Ok, nevermind I restarted the computer and the panels came back.  If anybody knows why they disappeared in the first place, or how you can get them back when that happens I'd be interested to know.

---

### Post by crimesaucer on 2007-07-17
Sometimes the panels disappear and won't re-appear after a restart. And also (at least for me), there will be no way to create a new panel in my Settings Manager...so...


What you can do is this:

click alt+f2 and then enter this command:

```
gnome-panel &
```


or if you use xubuntu xfce4 then enter this:

```
xfce4-panel &
```

I think the gnome part is correct, I use xubuntu so I just wrote "gnome-panel" the way I write "xfce4-panel", and the "&" part will keep them running.

---

