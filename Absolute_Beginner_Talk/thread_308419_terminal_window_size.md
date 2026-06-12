---
title: "terminal window size"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by saltyscott on 2006-11-28
is there any way to change the default size of the terminal when i open it?

---

### Post by richardward101 on 2006-11-28
the command for the terminal is gnome-terminal
the following command should open up a 30 cols * 30 rows terminal:
```
gnome-terminal --geometry=30x30
```
You can edit the menu entry to match your chosen size using smeg or alacarte, and right clicking on desktop/panel launchers allows you to alter the command.
Hope that helps

---

### Post by richardward101 on 2006-11-28
you can also change it under "preferred applications"

---

### Post by saltyscott on 2006-11-28
ok i got it to change under the panel launcher. the preferred applications one doesnt seem to change anything though.

---

### Post by richardward101 on 2006-11-28
The preferred applications is only used for times when applications need to be run from a terminal by nautilus, e.g. when you double click on a bash script and you click 'run in terminal'.

---

### Post by saltyscott on 2006-11-28
oh ok. i was thinking it would make it so the terminal is that size even if i dont change the launcher. thank you for your help.

---

