---
title: "Just Installed ZSNES ... I think"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by E.T.Expatriate on 2007-09-03
I just used synaptic to install the ZSNES emulator. However, though I can get it to activate through the command line, It doesn't show up in the Applications > Games drop down. Also, unlike the GFCE NES emulator, simply clicking on the ROM file doesn't activate it. Both of these are convenient functions, so how do I get them?

---

### Post by sumguy231 on 2007-09-03
You can add it to the menu with the alacarte menu editory, which should be under System -> Preferences -> Main Menu.

For the second thing, you need to associate the rom files with ZSNES in Gnome. But I don't know how to do that, I'm a KDE user mostly.

---

### Post by InGunsWeTrust on 2007-09-03
ZSNES hasn't implimented the function of clicking to open probably because it can run a zip containing the ROM and it would just be inconvienient if all of your ZIP files opened in an emulator. But to add ZSNES to your Applications menu simply right click the Ubuntu Logo in the top left corner. and select edit menus. Highlight Game under Applications and click the New Item button for the command enter what you enter at the command line to run it. Name it whatever you want and add a comment if you want. to add the zsnes icon to the launcher click on the square that is currently empty and put  /usr/share/pixmaps/zsnes32.png in as the path. I have the 64 bit version so it may simply be /usr/share/pixmaps/zsnes.png for you.

---

### Post by E.T.Expatriate on 2007-09-03
Thank You, and that's good general info to know as well.

---

### Post by Nikron on 2007-09-03
Well for me.. my zsnes files end with .smc.  So all I did was right click on them, hit properties, went to the "Open With" tab, and added zsnes as the command to open the file.  However, I do not use ubuntu as a desktop, so you have a different gnome version than me.

---

