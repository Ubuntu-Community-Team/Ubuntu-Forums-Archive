---
title: "utorrent window disappeared   :-I"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by darkdays on 2007-05-02
Installed uTorrent with wine today, worked fine until I left the window on one of the other viewports and exited the program using the small icon in the notifier area. Now no matter what I do I can't get the window to open on any of my viewports. When I start it it the notifier icon pops up, but clicking hide/show makes no difference, the program is running as I can see the stats updating, but the programs window seem to have been banished from my viewports.

Do anyone have a good idea of how to restore the window?
I'm using Compiz on Feisty.

edit>  found a thread that I didn't find earlier, hopefully I'll find my answer there.. sorry, can't seem to remove this.

---

### Post by Xarok on 2007-05-02
> **darkdays said:**
> Installed uTorrent with wine today, worked fine until I left the window on one of the other viewports and exited the program using the small icon in the notifier area. Now no matter what I do I can't get the window to open on any of my viewports. When I start it it the notifier icon pops up, but clicking hide/show makes no difference, the program is running as I can see the stats updating, but the programs window seem to have been banished from my viewports.

Do anyone have a good idea of how to restore the window?
I'm using Compiz on Feisty.

Sometimes I get problems seeing windows when using Beryl or Compiz. Try disabling Compiz

---

### Post by darkdays on 2007-05-02
Tried disabling compiz, not sure if it ever did, three times in a row it started up despite disabling it and restarting x.
Found this thread though that seems to be about my issue: 
[http://ubuntuforums.org/showthread.php?t=357885&highlight=utorrent+window](http://ubuntuforums.org/showthread.php?t=357885&highlight=utorrent+window)


<edit>

Worked out well, if anyone else have troubles with this try emptying this folder, and then don't use the minimize to tray setting:

/home/<username>/.wine/drive_c/windows/profiles/petter/Application Data/uTorrent

---

### Post by annda on 2007-05-02
i've been having a similar problem. maybe it's not exactly the same.

i even reinstalled wine before i discovered that the show/hide utorrent option in the notification area works. i understand it doesn't for you.

you could try showing the window and cycling through all the available viewports. i think it should show up in the windows list (another applet). if you get to a window skeleton with borders only, try the 'show/hide' option again.

i hope this helps. my troubles started after i installed beryl. now it's just a matter of an extra mouse click.

EDIT: i DID reinstall wine. maybe it's important. also, i tried other bittorrent clients, but nothing seems to work as well for me as utorrent, so the extra clicks are worth it.

---

