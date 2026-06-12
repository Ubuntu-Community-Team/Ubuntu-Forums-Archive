---
title: "Installs"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by spellico on 2007-01-07
I can't see several programs I installed using apt-get install or from the repository . Installation is fine and completed but i can't find the program on the panel. I also can't find bit-torrent. Obviously there's something fundamental I don't know. Any help? Thanks very much

---

### Post by Koybe on 2007-01-07
Sometimes after an install the gnome panel doesn't refresh. You can try logging off and on. Or you can open a terminal and type 
```
killall gnome-panel
```

If you still have problem you can also check in Applications->Accessories->Alacarte Menu Editor that evrything you need is ticked.

---

### Post by meng on 2007-01-07
Not every program necessarily comes with a menu entry. What have you installed?

---

### Post by Scorpuk on 2007-01-07
Might help us if you list the programs you installed.


Not sure about bit-torrent as I don't use it myself, but I'm sure soneone out there will know.

---

### Post by xpod on 2007-01-07
You can try running them from the terminal.
Some apps seem to  install ok but still need enabled via the menu editor(right click your menu`s)
Others might need you to create a menu option for them?

I usually install the debian menu which seems to show practically everything up although dont quote me on that;)

---

### Post by MkfIbK7a on 2007-01-07
dont quote me either ut after i installed both KDE and GNOME on my xubuntu the debian menu came on GNOME by itself...:mrgreen:

---

### Post by spellico on 2007-01-07
the programs are e-fax and clamav and now trying to reinstall brutalchess it gives me an error message "Dependency is not satisfiable:libc6" yet libc6 is installed , in fact I even reinstalled it... thanks

---

### Post by GreenHawkIA on 2007-01-08
I know clamav doesn't show in the menu list as it is a command-line program.

---

### Post by mlissner on 2007-01-08
bittorrent, if I recall correctly, is command line as well unless you get the gui front-end for it. Do this:

```
sudo apt-get install bittorrent-gui
```

I believe that will install the front end for it...optionally, you could check it out in synaptic and see what you think...I don't know a lot about torrents, but for some reason, azureus seems to be the torrent manager of choice from what I've gather.

---

