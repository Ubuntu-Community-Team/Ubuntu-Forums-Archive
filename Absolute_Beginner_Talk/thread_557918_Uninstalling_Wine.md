---
title: "Uninstalling Wine"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-23
Hi I have just uninstalled wine. This is how:

I deleted the .wine folder
Then in Synaptic I just selected the application for complete removal.

But now under the Applications menu Wine is still there. Why didn't synaptic remove that aswell.

So now there is: Applications>Wine>Programs>Steam etc.

Do I just delete this from the menu? And will that have uninstalled wine and steam properly?

---

### Post by dmber on 2007-09-23
i think you should have used synaptic first.  at least that's the way i understand it.  so i can't tell you the answer to your question...sorry.

---

### Post by Hobo Joe on 2007-09-23
Try this:
```

sudo aptitude purge wine

```

---

### Post by ROUBOS on 2007-09-23
just did it. Menu items still there.
I read somewhere that aptitude is better than apt-get and Synaptic but only if you used to to install the application. 

Just ran the command you gave me. This is what it did:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

The menu item is still there though. Is it OK to delete it from the menu. Wine looks like it's removed and that the menu is just holding the shortcuts

---

### Post by SOULRiDER on 2007-09-23
For some reason the menu entried didnt get removed, you will have to remove them manually. Just right click your applications menu and select edit. Find the entries you want to remove and uncheck them or delete them.

---

### Post by Hobo Joe on 2007-09-23
What happens when you try to run one of the shortcuts?

If nothing happens, I'd say it's perfectly safe to get rid of them.

---

### Post by overdrank on 2007-09-23
> **ROUBOS said:**
> just did it. Menu items still there.
I read somewhere that aptitude is better than apt-get and Synaptic but only if you used to to install the application. 

Just ran the command you gave me. This is what it did:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

The menu item is still there though. Is it OK to delete it from the menu. Wine looks like it's removed and that the menu is just holding the shortcuts

Hi for future reference
[http://doc.ubuntu.com/ubuntu/serverguide/C/aptitude.html](http://doc.ubuntu.com/ubuntu/serverguide/C/aptitude.html)
Just some info good luck!

---

### Post by FuturePilot on 2007-09-23
Just open the menu editor and delete the Wine Menu

---

### Post by asmoore82 on 2007-09-23
to be *perfect*, you should have run ``wine uninstaller''
first to get rid of all the shortcuts to wine software.

**Honestly**, I would have done *exactly* the same thing as you did.
I would say that "uninstalling" software that isn't even installed system
wide just to make sure the shortcuts get gone is a waste of time:p!

delete those rascals by hand: this command should help locate them...
```
**~$** find ~ -name "*desktop"
```

---

### Post by vinutux on 2007-09-23
Alt+F2  and type alacarte  ..............


look on it for removing and adding menus in gnome:guitar:

---

### Post by ROUBOS on 2007-09-23
OK I tried running steam from the menu. Nothing happened 
tried wine uninstaller and it said that wine is not installed.
So I went onto the menu editor (Gnome) and unticked it. should be fine then

---

### Post by asmoore82 on 2007-09-23
> **ROUBOS said:**
> OK I tried running steam from the menu. Nothing happened 
tried wine uninstaller and it said that wine is not installed.
So I went onto the menu editor (Gnome) and unticked it. should be fine then

I see what he meant with ``alacarte'' and **I like it ...**

right-click on menu-bar and ``edit menus`` -OR- run -> alacarte
then, you must pick the ``Applications'' toplevel menu in the left pane
and you can then right-click on the ``Wine'' folder and delete it in the right pane.

---

### Post by Kilz on 2007-09-23
> **asmoore82 said:**
> I see what he meant with ``alacarte'' and **I like it ...**

right-click on menu-bar and ``edit menus`` -OR- run -> alacarte
then, you must pick the ``Applications'' toplevel menu in the left pane
and you can then right-click on the ``Wine'' folder and delete it in the right pane.

or System >Preferences > Main Menu

---

### Post by asmoore82 on 2007-09-24
> **Kilz said:**
> or System >Preferences > Main Menu

Thanks! ;) it really is all about Freedom of choice.

---

