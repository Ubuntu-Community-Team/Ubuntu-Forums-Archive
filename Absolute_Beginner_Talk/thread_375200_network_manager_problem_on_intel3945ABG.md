---
title: "network manager problem on intel3945ABG"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by theytsejam on 2007-03-03
Hi all,
I've just installed ubuntu edgy on my Dell e1405 laptop (intel 3945ABG wireless card). My wireless card seems to work fine in that I can connect to known networks through the default ubuntu wireless program, but the gnome network manager doesn't work at all. I see the little icon on the bar at the top, but it shows a little red "x" at the bottom right and when I move my mouse over it it says "no network connection," even while I'm typing this message out connected to a local cafe's wireless network through the default program. When I click on the icon I only get a greyed-out "wired network" button. I know that my card is supposed to work out-of-the-box in edgy (indeed it seems to be right now), but is it possible that I have to install the [linux driver]("http://ipw3945.sourceforge.net/") anyway?
I'm not completely new to linux, but I'm also not that experienced (I'm not totally comfortable in the command line, for instance). So please forgive me if this is a dumb question or if I'm overlooking something obvious. Any help at all would be greatly appreciated!

Thanks,
Greg

---

### Post by teaker1s on 2007-03-03
system>administration>networking your devices must be unconfigured to allow
network-manager-gnome to handle them

---

### Post by theytsejam on 2007-03-03
Nice, it worked. Thanks teaker1s!

---

### Post by teaker1s on 2007-03-03
result:guitar: :guitar: :guitar:

---

