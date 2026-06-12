---
title: "Where are they?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by docmwj on 2006-06-07
Downloaded some games from the repository.
WHERE ARE THEY?

They aren't in the applications/games drop down menu.

Where do I look for these games?

Thanks said the newbie

---

### Post by aysiu on 2006-06-07
[http://www.monkeyblog.org/ubuntu/installing/#where_did_it_go](http://www.monkeyblog.org/ubuntu/installing/#where_did_it_go)

---

### Post by nalmeth on 2006-06-07
you can refresh your panel by entering
killall gnome-panel

They may still not show up. Do you know the names of the games?
hit ALT-F2 and enter them.

Or in the terminal, look in /usr/games or /usr/share/games or something.

You might want to install a little app called xfce4-appfinder. It's handy.

---

### Post by cogadh on 2006-06-07
Not all installations will automatically create entries on the applications menu, some of them are meant to be run from the console and others you may have to create the shortcuts yourself. look in /usr/games and /usr/share/games for the executable or launch scripts. If you can't find the games there, then look at the package properties in Synaptic, it will tell you what files what files were installed and where they are.

---

### Post by jive_turkey on 2006-06-07
The guy above has a good plan,
> look at the package properties in Synaptic, it will tell you what files what files were installed and where they are.
The easiest way, and most likely the noob way is to find the command to launch the game, then create a launcher on the desktop. If you like the toolbars, use the menu editor. Its graphically based and simple. I'm assuming you know this, but the command to launch the game is in the /bin/ directory so start looking there when you go through Synaptic.

---

### Post by nanotube on 2006-06-08
[QUOTE=jive_turkey]The guy above has a good plan,

The easiest way, and most likely the noob way is to find the command to launch the game, then create a launcher on the desktop. If you like the toolbars, use the menu editor. Its graphically based and simple. I'm assuming you know this, but the command to launch the game is in the /bin/ directory so start looking there when you go through Synaptic.[/QUOTE]
correction: the game executable will be either in /usr/bin, or in /usr/games . it will not be in /bin.

---

