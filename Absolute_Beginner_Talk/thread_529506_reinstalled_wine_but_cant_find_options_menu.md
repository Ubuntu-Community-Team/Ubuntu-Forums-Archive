---
title: "reinstalled wine but cant find options menu"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by LowSky on 2007-08-19
For some reason I un-installed wine, because of some headache I made. When I re-installed it none of wine's menus came back under Applications or under System-> Preferences. What did I do wrong?

---

### Post by gobbles414 on 2007-08-19
Hi LowSky,

I've had the same thing happen with Wine (and other apps). The first thing to do is restart your computer. If the menu entries do not return after that, try going system --> preferences --> main menu. See if the Wine launchers are unchecked. If so, give them check marks and they should appear. If that doesn't work either, open the terminal and type the following to do a COMPLETE uninstall of Wine:

sudo apt-get --purge remove wine

Then, restart your computer. You can then reinstall Wine from add/remove, Synaptic, or the terminal. Please post your results to this tread for the benefit of other Ubuntu users.

---

### Post by Megaqwerty on 2007-08-19
Just for future reference, you don't actually have to reboot your computer to get new menu entries to show up. you merely need to type: ```
killall gnome-panel
``` and the panel will disappear, and then reappear after a second or two.

---

### Post by LowSky on 2007-08-19
> **gobbles414 said:**
> Hi LowSky,

I've had the same thing happen with Wine (and other apps). The first thing to do is restart your computer. If the menu entries do not return after that, try going system --> preferences --> main menu. See if the Wine launchers are unchecked. If so, give them check marks and they should appear. If that doesn't work either, open the terminal and type the following to do a COMPLETE uninstall of Wine:

sudo apt-get --purge remove wine

Then, restart your computer. You can then reinstall Wine from add/remove, Synaptic, or the terminal. Please post your results to this tread for the benefit of other Ubuntu users.



Did all that and still nothing...very wierd

---

### Post by Megaqwerty on 2007-08-19
Well, now that it's installed again, check **System>Preferences>Main Menu** again, and see if it's in there. If worst comes to worst, you can use that program to make new menu entries.

-Megaqwerty

P.S. The command for the WINE configuration editor is ```
winecfg
```

---

### Post by gobbles414 on 2007-08-19
LowSky,

Uninstall Wine again and then try going system --> administration --> software sources --> updates --> unsupported updates (backports). In addition to giving you updates to other programs on your system, you will also gain access to a newer version of Wine. Worth a try IMHO...

---

### Post by LowSky on 2007-08-19
> **gobbles414 said:**
> LowSky,

Uninstall Wine again and then try going system --> administration --> software sources --> updates --> unsupported updates (backports). In addition to giving you updates to other programs on your system, you will also gain access to a newer version of Wine. Worth a try IMHO...


Thanks this helped but in another way...

What I had to do was removed the WINE repositories under the Third- Party Software tab in Software Sources. Then restarted gnome and all was fine...

Still seems very odd to me that that was the problem.

Now I can reinstall Counter Strike...  :lolflag:


Thanks Everyone for helping... This is why I love Ubuntu.

---

