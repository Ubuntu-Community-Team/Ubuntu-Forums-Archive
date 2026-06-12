---
title: "Gnome_panel"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by code_08 on 2005-06-02
Well i was messing around with the little bar at the top (moving it around adding shortcuts) After i got done i realized that it would not go back to the way it was. I tryed uninstalling it and then installing it again from terminal but it's stil the same, all the stuff is smashed together on the righthand side. I am wondering if there is any way to set the panel back to the default settings. I found the panel-default-setup.entries thing in the schemas folder but i can't figure out how to run this or if you can

---

### Post by Psquared on 2005-06-02
[QUOTE=code_08]Well i was messing around with the little bar at the top (moving it around adding shortcuts) After i got done i realized that it would not go back to the way it was. I tryed uninstalling it and then installing it again from terminal but it's stil the same, all the stuff is smashed together on the righthand side. I am wondering if there is any way to set the panel back to the default settings. I found the panel-default-setup.entries thing in the schemas folder but i can't figure out how to run this or if you can[/QUOTE]

Just delete/remove what you have put on the taskbar or the gnome bar by right clicking on it. You can also remove the bar entirely.

---

### Post by NewbieNik on 2005-06-02
[QUOTE=code_08]Well i was messing around with the little bar at the top (moving it around adding shortcuts) After i got done i realized that it would not go back to the way it was. I tryed uninstalling it and then installing it again from terminal but it's stil the same, all the stuff is smashed together on the righthand side. I am wondering if there is any way to set the panel back to the default settings. I found the panel-default-setup.entries thing in the schemas folder but i can't figure out how to run this or if you can[/QUOTE]

It might be worth trying the:-

killall gnome-panel

in the terminal. This should refresh the panl, but I'm not sure if it resets it. Worth a go.

---

### Post by code_08 on 2005-06-02
[QUOTE=NewbieNik]It might be worth trying the:-

killall gnome-panel

in the terminal. This should refresh the panl, but I'm not sure if it resets it. Worth a go.[/QUOTE]

I have tried both and i still want the bar i just want it to be set back to default. The killall command just refreshes it so that doesn't really help.

---

### Post by code_08 on 2005-06-02
[QUOTE=code_08]I have tried both and i still want the bar i just want it to be set back to default. The killall command just refreshes it so that doesn't really help.[/QUOTE]
 another problem i have is when i tryed to play a dvd it was all slow and skippy like it wasn't reading the disc fast enough any help would be great

---

### Post by betrayed on 2005-06-02
[QUOTE=code_08]another problem i have is when i tryed to play a dvd it was all slow and skippy like it wasn't reading the disc fast enough any help would be great[/QUOTE]
 sudo hdparm -d1 /dev/hdc (or whatever your dvd drive is)

---

