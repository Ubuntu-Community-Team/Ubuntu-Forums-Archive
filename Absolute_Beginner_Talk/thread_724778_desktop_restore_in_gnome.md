---
title: "desktop restore in gnome"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-15
In KDE, if you shut the computer down and restart it, it will restore all the programs you had open. Is there any way to enable this in Gnome?

---

### Post by FreewareFan on 2008-03-15
While you have your programs open, go to System - Preferences - Sessions.  When that opens, click the Session Options tab, and check the box for Remember running applications on shutdown.

That will do it.

FwF

---

### Post by BetterSense on 2008-03-15
Thanks a bunch. Something tells me it's not smart enough to put them on their respective desktop cube faces though; I'll have to try it.

---

### Post by glennric on 2008-03-15
You can do that with compiz.  Open the System->Preferences->Advanced Desktop Effects Settings.
If you don't have that type
```
sudo apt-get install compizconfig-settings-manager
```
then you will.
Then find the "Place Windows" plugin under Window Management, and look under the Fixed Window Placement tab.

---

### Post by BetterSense on 2008-03-15
I went there bt I don't understand what i need to do. I see two blank spaces for 'windows with fixed placement' and 'windows with fixed viewport'. What am I supposed to do?

---

### Post by forrestcupp on 2008-03-15
In the main screen, just make sure the box next to 'Place Windows' is checked.  When you click on 'Place Windows' in the General tab make sure the drop down box says 'smart'.

But the fix you did in Sessions is what you really were wanting.

---

### Post by BetterSense on 2008-03-16
Regardless of whether Place Windows works, the desktop restore is just not worknig. I definitely have checked 'Automatically remember running applications when logging out'. I can open a handful of programs, restart, (cold, soft, xserver only doesn't matter) and the programs don't come back.

---

### Post by FreewareFan on 2008-03-18
OK, in that case, those programs are not what is called" session managed."

What I would do then, is to get a list of all the programs you want to be running when you do a login, and then enter those programs in the Startup tab of the Sessions manager.  I know for sure it will work for you then!

FwF

---

