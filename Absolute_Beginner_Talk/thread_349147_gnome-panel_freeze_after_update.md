---
title: "gnome-panel freeze after update"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2007-01-29
I just updated gnome-panel and I'm using it with beryl. It always says another panel is running but ```
 killall gnome-panel 
``` fixed that. Now as it reloads the panel it stops halfway. It loads all the icons left of the red power icon. :confused:  None of the icons it loads are usable and rightclicking does nothing. 

Any ideas?

Thank you.

---

### Post by CurlyChris on 2007-01-30
Got a similar problem here too, this time on a laptop running standard Edgy.

After the update, the top panel only had an icon for Tomboy (that I'd previously added) plus wireless indicator in the system tray; the bottom panel only showed the wastebasket.

Pressed Ctrl+Alt+Backspace to restart X and after logging in now get the message that another panel is running, click ok, then get this again another 6 times before the desktop comes up with no panels at all!

Fortunately I'd previously added KDE so can at least get a usable desktop but is there a way to reinstall the previous version of the gnome-panel?  I've been trying to force a downgrade using Synaptic but can't get it to work for me...

Thanks.

Chris

---

### Post by Skidlz on 2007-01-31
Downgrade didn't work here either. But I am able to use alt+tab, terminal and kiba-dock to get to everything. If you want a panel you can use fbpanel
```
 sudo apt-get install fbpanel
```

---

### Post by CurlyChris on 2007-02-01
Thanks Skidlz.

I actually restored a previous image of my / partition and then updated again, this time leaving out the gnome-panel and associated updates.  I'm not going to mess with it now as it's working fine and I haven't got time to play with it at the moment - maybe in a few weeks.

Cheers

Chris

---

