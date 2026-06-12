---
title: "Where do I find my newly downloaded program?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by RobHK on 2007-12-15
I have a little gripe with Ubuntu, which is that after downloading a new program I don't always know where the shortcut is, or even if there is one. (I can probably run the app from a command line, but as yet I don't know how to do this, and would really prefer not to have to. Like many potential converts from Windows I go rushing back to Bill as soon as someone suggests I use the command line!  

The particular program I have just installed is xjig (from Synaptic Package Manager).

[Edited later]

OK I did the obvious and typed xjig into a command line! Never imagined it would work that simply!, but can I put the new program into a Menu under Applications?

[Edited again]

You guys are certainly quick off the mark! Thanks for all your help.

---

### Post by daimaru on 2007-12-15
if you hit alt+f2 and enter xjig does it start, if yes you can start it that way. since some progs dont create startmenu entries you will have to add one yourself. hit alt+f2 enter alacarte or rightclick your applicationsmenu hit "edit menu" select a suitable category and then add a "new item". as the command enter xjig for comments etc choose whatever you like. if you like to assign an icon click the icon box on the left.

---

### Post by buzzmandt on 2007-12-15
from command line type > xjig
press enter

---

### Post by CatKiller on 2007-12-15
Sometimes they do create menu entries, but the menu needs to be refreshed for the entry to appear. **Alt-F2** and **killall gnome-panel** will cause the panel to restart, refreshing the menu.

---

### Post by philinux on 2007-12-15
Right click on application - choose edit menus.

Select the group then select New Item. Give it a title and put the command in. Sorted

---

