---
title: "[SOLVED] Please tell me step-by-step instructions- How do you add columns via the pan"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-17
[color="Green"][b]I tried to follow those instructions (seen below), but I don't see the option that says "preferences" when I right click on the panels.

1. Would you tell me if I have to select either: "Add to Panel", "Properties", or "New Panel" when I click on the right-corner of my screen?
2. How do you add columns via the panel?
3. Once I add columns, would the 3D Cube-effect work?[/b][/color]

These instructions are in reference to this forum-thread:
[Would you please help me get the 3D-Cube effect in Ubuntu 7.04?](http://ubuntuforums.org/showthread.php?p=4349218)

> **jan quark said:**
> right click on the two existing desktop panels in the right corner of the screen
then preferences
then add two more columns so you have four

---

### Post by drs305 on 2008-02-17
I think what you are asking for is to be able to view the workspace switcher - or at least have 4 panels. The right clicking to get to Properties requires that you see the 2 panels (from your previous post). Try running this to see if the workspaces show up in the bottom right corner of your monitor:
```
gconftool-2 --type bool --set /apps/panel/applets/workspace_switcher_screen0/prefs/display_all_workspaces true
```

All the settings are accessible via gconf-editor  (from terminal). You can drill down the menu following the path specified above if you prefer GUI.

If you don't get it or want to return to what you had, change true to false.

---

### Post by Erkenntnis on 2008-02-17
You have to right-click on the window switcher itself (which is one of the applets on your panel) and select preferences, not on the panel.  By default, it's in the lower-right hand corner of the screen near the trash can.

---

### Post by ahuman on 2008-02-17
> **drs305 said:**
> I think what you are asking for is to be able to view the workspace switcher - or at least have 4 panels. The right clicking to get to Properties requires that you see the 2 panels (from your previous post). Try running this to see if the workspaces show up in the bottom right corner of your monitor:
```
gconftool-2 --type bool --set /apps/panel/applets/workspace_switcher_screen0/prefs/display_all_workspaces true
```
All the settings are accessible via gconf-editor  (from terminal). You can drill down the menu following the path specified above if you prefer GUI.
If you don't get it or want to return to what you had, change true to false.

[COLOR="Blue"]**Do I have to restart after I run that command? The Windows Switcher option did not appear anywhere on my screen or desktop when I ran that command.**[/COLOR]

---

### Post by drs305 on 2008-02-17
Running the gconf-tool I mentioned didn't work- seems to be overridden by another setting I've enabled. The column option in the same subset reacts instantaneously. Let me see what I can find.

Edited: I'm running Gutsy and the switcher is controlled by Advanced Desktop Effects, which I think is new or different in Gutsy. I'll have to leave this to guys/gals running Fiesty. Good luck.

---

### Post by ahuman on 2008-02-19
[COLOR="Magenta"][B]I'm _not_ running Feisty, but I do have Gusty (7.10) on my computer. I'll go to the Advanced... section you mentioned. Do you or anyone else have the 3D-cube feature on your computer(s)? I'm still only getting the "two-sided"-effect, rather than the 3D-cube (4-sided-effect).

Please give me step-by-step instructions.[/B][/COLOR]

---

### Post by oldos2er on 2008-02-19
At the bottom right-hand corner of your screen, you should see 2 squares next to your trash icon. Do you?

---

### Post by ahuman on 2008-02-19
[COLOR="Blue"][B]No, Those 2 squares haven't been there ever since I got Ubuntu Gusty 7.10 installed on my computer. If you want to, please view the bottom of the following screenshot provided below this message.

If you or someone else knows how to make those 2 squares appear, please tell me how I can get those 2 squares to appear near my trash-icon?[/B][/COLOR]

Click to Enlarge screenshot:
[[img]http://img227.imageshack.us/img227/8683/screenshotrw9.th.png[/img]](http://img230.imageshack.us/img230/391/screenshotbg3.png)

---

### Post by ahuman on 2008-02-19
[COLOR="Red"]:) I would appreciate more help to get the 3D-Cube effect. Thanks for your time & patience, all of you, who come here to assist beginners/ignoramuses like me.

The option, which I was told allows you to add columns or panels to make the 3D-effect work on my computer doesn't seem to be anywhere on my desktop.

1 more question about the 2 squares that were mentioned on this forum-thread: Are they seen on your desktop?[/COLOR]

---

### Post by teamkiller87 on 2008-02-19
In order to get the "2 squares" right click the panel and choose Add to panel. In the Desktop & Windows section you should see something like "Workspace Switcher". I don't remember how many desktops are available by default but to increase the number or change the layout you can right-click on the squares and choose preferences to define the layout of your workspaces in columns and rows. In order for the 3d cube to work you need 4 columns and 1 row. That is if you've already installed and configured Compiz. That's a whole different story.

---

### Post by ahuman on 2008-02-19
[COLOR="DarkBlue"]**Since I've already installed and configured Compiz, would any of you please tell me how I can get those 2 squares or 2 new columns (or 2 new desktops) to appear on my Ubuntu OS screen/computer monitor? *or* Would you at least tell me the easiest way to get the 3D-cube effect to work on my computer (which is running Ubuntu/Gusty 7.10)?**[/COLOR]

---

### Post by drs305 on 2008-02-19
ahuman,

Did you try what teamkiller87 said. You should have a panel that runs along the bottom of your computer. It is where the apps that you have open are shown (not shortcuts which are usually at the top). Right click on any empty area of that bottom panel. At the top of the menu that opens, you should see + Add to Panel.  Click on this. In the Desktop & Windows section, probably in the lower right of that section, can you see a listing with a blue and white square called "Workspace Switcher"? If you select that, it should put a two pane rectangle in the lower right corner of the lower panel. Once you see that, you should be able to right click within that rectangle, select Properties, and change the columns to 4. 

If you can do this then we can start work on the desktop cube.

---

### Post by ahuman on 2008-02-20
[COLOR="DarkRed"]**Thanks.I read all of that, I appreciate you. That worked for me.**[/COLOR]

---

