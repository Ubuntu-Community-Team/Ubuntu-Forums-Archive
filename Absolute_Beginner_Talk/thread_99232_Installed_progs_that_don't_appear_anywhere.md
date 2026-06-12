---
title: "Installed progs that don't appear anywhere"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by arbalest on 2005-12-05
I'm fairly new to anything non-windows and I'm enjoying Ubuntu but I've hit a few bumps:

1 - I wanted a download manager and so I installed GWGET with Synaptic but it doesn't appear in any program menus, ie, "Internet". How do I find it and get it into the main menu?

2 - I've really hit the wall with the whole Mythtv project thing. First of all, I've installed every Myth and DVB-T item I could find in any repository but, as above, they don't show up anywhere. Also I've just bought a Twinhan Magic Box II USB2.0 Digital TV tuner and the results in Windows are phenomenal (free-to-air digital tv, Melbourne). I've found a page here -

[http://www.linuxtv.org/wiki/index.php/DVB_USB#Twinhan_DVB-T_USB2.0](http://www.linuxtv.org/wiki/index.php/DVB_USB#Twinhan_DVB-T_USB2.0)

- that suggests that there are drivers for this tool but I can't find them and I'm not sure what I'd do with them if I did.

I divided this post into two questions and I'm pretty sure that the first question is easy and the second is a nightmare, or just too broad a question.  But I'd really love to know if anyone has built a MythTv box with an external Twinhan device. Any advice would be welcome. Thanks.

---

### Post by Hendry on 2005-12-05
[QUOTE=arbalest]
1 - I wanted a download manager and so I installed GWGET with Synaptic but it doesn't appear in any program menus, ie, "Internet". How do I find it and get it into the main menu? [/QUOTE]

Just click with right mouse on the Applications menu and select edit menus. Now you can add additional software or rearrange the menu

---

### Post by gonçalo on 2005-12-05
Hello arbalest


I can only shed some light on your first problem, the second is too esoteric for me.

Sometimes the gnome panel doesn't refresh and new apps don't get listed. I have gwget installed and 
Gwget is listed in Internet under the name of Download Manager, and you can check if it's there or you can:
 open a terminal and type gwget and press return

or

 ALT+F2 type gwget and press return


to update your panel, if I'm not mistaken, at a terminal type:

killall gnome-panel

after wich you'll be able to see Download Manager in your gnome panel.

---

