---
title: "Renaming menu items."
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-03-02
This seems like it should be so simple. I'm starting to suspect it is a bug and not my lack of experience but I figured I'd check here to make sure I'm not doing something retarded.

I installed Unreal Tournament 2004 in Breezy 5.10. No trouble there. It installed a menu item under "Other" called "ut2004".

It's a game, so I'd like it under the "Games" section so I right click on my menu, go to "edit menu" or whatever (I'm not at that computer now) and moved it into the "Games" menu. So far so good.

I'd like to give it a more friendly name than "ut2004" so I right click it and go to properties. I change the first field (I think it's description or something) to "Unreal Tournament 2004," the second (comment?) to "Play Unreal Tournament 2004" and close the window.

It never changes the name of the item in the menu, though, and the comment doesn't show up on mouse-over. When I go back to the editor the changes are exactly as I made them. Am I skipping a critical step?

Mostly I'm just happy that I managed to install, patch the game and make it work. This is a minor annoyance but I'd like to get to the bottom of it.

---

### Post by bluevoodoo1 on 2006-03-02
Hmm... After you change it, how about

killall gnome-panel

to refresh the panel/menu.

---

### Post by pbaehr on 2006-03-02
I'll give that a shot, though, the computer has been restarted since I made the change and it continues to show the old menu item name. I'm assuming this would in essence accomplish the same thing.

---

### Post by WackToMack on 2006-03-02
The same thing used to happen to me before the menu editor started getting errors... Whenever I tried to rename a shortcut in the menu, it wouldn't change... so I downloaded kmenuedit via Synaptic and use that to rename my shortcuts. :D

---

### Post by pbaehr on 2006-03-02
Does kmenuedit work in Gnome? I notice it's developed for KDE.

---

### Post by Sweet on 2006-03-02
[QUOTE=pbaehr]Does kmenuedit work in Gnome? I notice it's developed for KDE.[/QUOTE]

Try smeg for menu editing (works with GNOME, KDE, and XFCE) :D

---

### Post by pbaehr on 2006-03-02
Thanks! I'll try it!

---

### Post by pbaehr on 2006-03-04
Apparently smeg is the default menu editor in Ubuntu so that is the exact program that is giving me the problem.

Is there a configuration file somewhere I can edit by hand?

---

### Post by Sweet on 2006-03-06
Yes there is, but im sorry I cant remember where :oops: 

Maybe someone else can post the location for you :D

---

### Post by WackToMack on 2006-03-06
Yep, kmenuedit works in Gnome.  :D

---

### Post by cstudent on 2006-03-06
The menu config files are usually found under /usr/share/applications/ or may be under some sub-directory of that path. Look there for a .desktop file that concerns your program. Open it in a text editor using sudo. I think the category you want to place it in would be games, but you can open another game .desktop file and check how that one is configured to get it right.

---

### Post by pbaehr on 2006-03-06
Nice. Thanks.

I did end up experimenting with kmenuedit but found it was displaying something other than my menu. The application in question did not show up where it currently was and moving it there and saving did nothing. I didn't mess around with it for too long.

I think I'd rather just try and find the configuration files. I don't mind getting a little virtual dirt on my hands. I'll try that when I get home from work.

Thanks for the info on the location to look at.

---

