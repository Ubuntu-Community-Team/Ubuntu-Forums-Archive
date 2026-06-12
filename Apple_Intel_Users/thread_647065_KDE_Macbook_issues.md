---
title: "KDE Macbook issues"
date: 2007-12-21
forum: Apple Intel Users
---

### Post by DGortze380 on 2007-12-21
Hey guys,

I'm hooked, I've been using Ubuntu on my Macbook full time for almost 5 months now and I love it (still dual booting just in case as I've screwed a few things up and had to reinstall)... anyways, I'm learning the command line pretty quick but still like to have a GUI for everyday stuff.  I installed KDE the other day (still have Gnome too), and I like KDE better but I have a few questions...

1)  Is there something similar to "Mouse Keys" from Gnome in KDE?  I haven't been able to find a way to get right-click activated in KDE.

2) Is there a Recent Documents menu anywhere?  If so where?  And how do I clear it out? It's useful to get to things quickly, but having it too full is a bit of a pet peeve of mine.

3) Compiz Fusion doesn't seem to work in KDE (it was up and running in Gnome). It's already installed, and I even have the Advanced Desktop Effects in the menu in KDE, but no matter what I change I can't get them working.

I think those are my only issues right now, any help would be appreciated, I'd love to get KDE to a point where I can use it full time instead of Gnome.

---

### Post by Whiffle on 2007-12-21
1) No idea.

2) You can add a recent docs menu to your kmenu if you like,  Right click the panel, unlock panel, Panel menu, Configure Panel, Menus, and then check Recent Documents in the optional menus box.  As far as clearing it goes, i dunno, i never use it.

3) Its probably not starting when you run kde.  To test it, hit Alt+F2 and run "compiz -replace" and see if it works.  If you search the internet/forums there are a few ways to get compiz to start.  What I used to do when I ran compiz is to set KDE so that it loads a saved session every time, and then when I have Compiz running, I save the session.  It then starts it every time.

---

### Post by DGortze380 on 2007-12-21
Ok, thanks for the advice. Need to figure out this right-click issue before I can add the Recent Documents, but I suspect it will work just fine once I figure that out.

compiz-replace returns "could not run" in terminal it returns "command not found"

I'll keep looking but I haven't been able to find anything on the forum that works to fix this. :-\

EDIT:
[B]
Mouse Keys Fixed, I can right click from the keyboard now.  Recent Documents Added.  Still can't figure out Compiz.[/B]

---

### Post by Whiffle on 2007-12-21
[http://www.linux.com/feature/58044](http://www.linux.com/feature/58044)

maybe?

---

### Post by DGortze380 on 2007-12-21
thanks for the idea, but tis an Intel not a PowerPC

---

### Post by cyberdork33 on 2007-12-22
the command should be 
```
 compiz --replace
```

---

