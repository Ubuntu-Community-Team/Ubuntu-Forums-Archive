---
title: "Desktop effects"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by doomed on 2007-07-09
I installed Ubuntu 7.04 2 days ago. I followed the steps on the Ubuntu wiki on installing beryl- it all worked ok... Untill I rebooted this morning. 

-This has happened to my workplace switcher panel:
[[IMG]http://img405.imageshack.us/img405/3929/screenshotpw3.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshotpw3.png)
-If I select the gnome window manager I loose all window bars, borders etc.
-and even with the special effects working, under desktop effects they appear off and if I turn them on it says that it can't enable desktop effects

my video card is a geforce 7300gt if that helps

Whats happening and how do I fix it? 
Thanks

---

### Post by Redache on 2007-07-09
Try turning Beryl Off. If you go to Sessions in the GDM (the initial Login Screen) and switch back to a default gnome. 

If you can file a bug report.

---

### Post by doomed on 2007-07-09
Well I don't mind what is happening at the moment, and I don't want to get rid of beryl, so I guess I'll just live with it. 
I just thought they're might be a solution.

---

### Post by bdtgp on 2007-07-12
Follow the instructions on this thread for installing it: [Compiz Fusion HowTo]("http://ubuntuforums.org/showthread.php?t=481314")
You're probably running the i386 (32-bit) version so only add the stuff for that.

Once you have it installed hit Alt+F2 and enter:
```
compiz --replace &
```

Then you should be good to go.

---

### Post by slughappy1 on 2007-07-15
Go to Applications -> Add/Remove and install Beryl Manager and Beryl Settings Manager.  When I installed the two programs it fixed all the bugs I had with the Desktop Effects and allowed me to configure all aspects of the effects.   Nothing crashes and everything so far works perfectly

---

