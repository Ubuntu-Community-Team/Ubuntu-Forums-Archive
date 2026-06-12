---
title: "custom Shortcut Icons on desktop how to remove the Arrows?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by SabrinalovesUbun2 on 2007-09-19
custom made Shortcut Icons on desktop how to remove the Arrows?

I made a few cartoon ".png" files, put each one in a seperate folder, and changed the properties of each folder that contains an image, so that the folder looks like the image.

all these folders are in "home"

so now I made shortcuts to each of these folders (that look like cartoons) and put them on the desktop

but the arrows on each cartoon don't look nice

please how can I remove them, thx

---

### Post by ryanVickers on 2007-10-03
There is no real way, but if you were to edit the shortcut arrow picture in /usr/share/icons/Human and all it's subfolders to be blank, then they wouldn't show up anymore :)

---

### Post by SabrinalovesUbun2 on 2007-10-04
> **ryanVickers said:**
> There is no real way, but if you were to edit the shortcut arrow picture in /usr/share/icons/Human and all it's subfolders to be blank, then they wouldn't show up anymore :)

ooo, weel maybe I wudn't wanna mess wit dat.

---

### Post by knobuddixspexdazpanishin on 2008-01-07
First off a word of caution: When browsing the File System via Nautilus we are reliant on knowing what's a shortcut and what's not. That's why removing them (AKA making them completely transparent) is unwise.

A far better alternative is to modify them by scaling the size down to 50% and add at the most 20% transparency (yes 20% is really all you'll need) and this combination will make them almost imperceptible....

So here's what you do:
1. **Always** make a backup before editing any system files: (if there's a problem you still have the original files). At the terminal shell type:
[COLOR="Indigo"][SIZE="2"][FONT="Trebuchet MS"]sudo cp -r /usr/share/icons/Tango/scalable/emblems/ /usr/share/icons/Tango/scalable/emblems-bu[/FONT][/SIZE][/COLOR]

2.  Navigate to /usr/share/icons/Tango/scalable/emblems/ and open emblem-symbolic-link.svg with Inkscape.

3. Select all, turn the master transparency down by 20% and scale the image to 50% of it's size.

4. in this example I saved the modified emblem-symbolic-link.svg in a separate directory at "home/myname/" called "scalable"

5. Go back to the terminal shell and type:
[FONT="Trebuchet MS"][SIZE="2"][COLOR="Indigo"]cd scalable[/COLOR][/SIZE][/FONT]
then
[FONT="Trebuchet MS"][SIZE="2"][COLOR="Indigo"]sudo mv emblem-symbolic-link.svg /usr/share/icons/Tango/scalable/emblems/[/COLOR][/SIZE][/FONT]

Restart your computer to see the changes.

There are other shortcut arrows located in /usr/share/icons/Tango/16x16/emblems/ , and 
22x22, 24x24, 32x32: four in total, called emblem-symbolic-link.png which can be edited with the Gimp at 50% scale with 20% transparency too if you find they are being used by your system, but remember to follow the steps above and make sure you back up a copy of the original folder first.

cheers :KS

---

