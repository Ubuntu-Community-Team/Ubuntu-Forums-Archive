---
title: "gnome-panel items not behave weird"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by startherepodcast on 2008-02-09
I run Ubuntu 7.10 and I have got a problem with my gnome-panel:
I used to be able to right click e.g. my skype icon and do stuff like change my status or quit. Now I am not able to do this anymore.
Whenever I right click an icon up in the notification area, I get the GNOME Menu saying stuff like "Get Help Online" or "Translate this Application". This turns out to be a pain in the *** if you have an Application without a Window (e.g. KTorrent) and you want to quit it. I always have to find out the pid and kill the App manually. 

That Sux. Anyone know a solution?

Edit: Reminder for myself: Check the title before submitting, think before you click

---

### Post by erfahren on 2008-02-09
it sounds like the notification applet configuration file got corrupted 

this is what I'd try first - remove the applet, just right-click on it and "remove" (or delete)

open your home folder and press Ctrl+H to view hidden files/folders - find the directory: .gconf/apps/panel/applets/notificationarea_screen0

rename that "notificationarea_screen0" to "notificationarea_screen0_back" (or rename the file in it)

right-click on the panel again and find the "notification tray" applet (or possibly similar to that) and add it again - you might need to quit and relaunch any programs that were in it

(actually - you might want to quit the programs in it ahead of time just so it starts empty)

---

### Post by startherepodcast on 2008-02-09
```
adzon@adzon-portable:~$ cd /home/adzon/.gconf/apps/panel/applets/notificationarea_screen0
bash: cd: /home/adzon/.gconf/apps/panel/applets/notificationarea_screen0: No such file or directory

```

So I just deleted the whole content of the /applets folder, except for gconf.xml (thought that might be important)
But nothing happens. I can't even double click the icons to bring them back or switch to their current viewport

---

### Post by erfahren on 2008-02-09
> **startherepodcast said:**
> ```
adzon@adzon-portable:~$ cd /home/adzon/.gconf/apps/panel/applets/notificationarea_screen0
bash: cd: /home/adzon/.gconf/apps/panel/applets/notificationarea_screen0: No such file or directory

```

So I just deleted the whole content of the /applets folder, except for gconf.xml (thought that might be important)
But nothing happens. I can't even double click the icons to bring them back or switch to their current viewport
I meant to right-click on the applet in the panel and remove it

- then go and rename the config file for it and then recreate the applet

if you deleted that whole directory it should still be in your trash - your panel applet for it might not work

go back into your home folder and browse to your .Trash folder (its hidden) and see if the directories you deleted are in there and restore them

---

### Post by startherepodcast on 2008-02-09
Sorry for being inaccurate there. There was no directory in the first place, so I just deleted the ones that were there (something like applet_0, applet_1 and something about cpu scaling). I had to resetup my clock but thats fine. 
I removed the applet before doing all this and rebooted and everything.

Still nothing...

I attached a screenshot so you can see what it looks like.

---

### Post by erfahren on 2008-02-10
if you're still having trouble with it you could try redoing the whole panel. All the items on it are merely applets (or launchers) and can be re-added.

you can do it this way - first just right-click on one of the panels and select "New Panel" - the new panel will end up on one of the sides for now. Right-click on it and select "Add to panel" - add the following (the order doesn't matter):
Menu Bar
Notification Area
Clock 
Quit

Right-click on the top panel and "Delete" - right-click on the new panel - select "Properties" and set the orientation to "Top" - now you can move the applets to where they go and lock them in place.

you can add the launchers that were there (Firefox, etc.) by finding them in the menu - right-click and "Add launcher to panel" (you probably know that already).

-- Looking closer at that screenshot it looks like you're using Compiz - and maybe some kind of snow effect. That may be interfering somehow. Maybe a Compiz update caused a bug. You could try disabling that and see if it works then - so you'll know if it's the cause.

---

### Post by startherepodcast on 2008-02-10
It's still the same.
I created a new panel, added everything I like, nothing.
Indeed I use compiz fusion, but it used to work before with it. Also I switched back to metacity (default window manager) and it was the same. THe snow effect is actually just my wallpaper.

I thought about removing the gnome-panel package and reinstalling it but I am not sure if that's a good idea yet...
could I try deleting the whole panel folder in gconf? maybe that helps...

---

### Post by erfahren on 2008-02-10
someone posted this tip on another thread - it was kind of what we were trying but it includes more of the configration files - [How to Reset Ubuntu/Gnome Settings to Defaults](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

something would have had to get really messed up to corrupt something with the gnome-panel outside of your user's configuration files.

---

