---
title: "fluxbox problems..."
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Nolander on 2008-01-24
Ive installed Fluxbox and most things are good, but i still have a few problems...

1. When i log into flux after restarting my computer it wont connect to the internet, i have to login to gnome then out then into flux. this can probibly be solved be putting a command in appsflux but i dont know wat command.

2. i get a message when i login and it ask if i wanna use X settings or Gnome setting, how can i make it choose X automatically

3. When i use gedit(note pad) it starts gnome or something like that and i cant use the right click menu, y?

4. and last how can i disable touch click?

thanx,

-nolander

Edit: the menu(right click) stops working once everything is loaded.

---

### Post by whayong on 2008-01-24
I'm ASSuming you installed fluxbox over a standard Ubuntu install.  What you need to do is to get Gnome to play nice with Fluxbox.  When you start those gnome apps, they are starting a gnome session as well which is why your right click menu no longer works.  I'm not an expert, or anywhere near it.  I'm just talk from experience with my fluxbox over ubuntu install.  

1.) For your network problems, my only suggestion would be to try and use WICD.  It seems to work well with my fluxbox install.  Downside to this is that you will have to remove gnome-network-manager.

2.) Before typing in your user name and password in the login screen.  Select options then select your session.  Aftrer logging in it will ask if you want that to be your default session.

3.) See above.

4.) I dont know.

Good luck!

---

### Post by cknight on 2008-01-25
> **Nolander said:**
> 
Edit: the menu(right click) stops working once everything is loaded.

This is likely to be a problem with your ~/.fluxbox/keys file.  Can you post it here? If you've used Fluxkeys to modify your keys file then in all liklihood it will have been corrupted.  You can check if this is the case by looking for "MouseTop" entries in this file.  Once we see what you have we can sort you out.

---

### Post by RedSquirrel on 2008-01-25
I know for certain you will loose the right-click Fluxbox menu if you run nautilus without the '--no-desktop' option. The "proper" way is:

```
nautilus --no-desktop
```

I'm not sure if other applications cause the same problem (I haven't used anything GNOME-based in a long long time, so things may have changed).

Are you starting any programs in your ~/.fluxbox/startup file?

It could also be the keys file problem mentioned by cknight.

---

