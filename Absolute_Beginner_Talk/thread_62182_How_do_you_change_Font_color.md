---
title: "How do you change Font color??"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-09-03
Looked high and low but can't figure it out. Help!!

---

### Post by sumadartson on 2005-09-03
Could you be a bit more specific?  :) 

For instance, do you mean font color in LaTeX / OpenOffice / Gnome Applets / KDE / XTerm / HTML / the forum / Enlightnement / etc...

I probably won't be able to answer your question, but if you make your question a bit clearer, someone else might. For your reference, see [the FAQ](http://ubuntuforums.org/faq.php?)

---

### Post by Lux Perpetua on 2005-09-03
[QUOTE=grofaz]Looked high and low but can't figure it out. Help!![/QUOTE]If you want to change the font colors for your applications, then that is handled by your GTK theme. Go to System->Preferences->Theme from the top panel, and try out some of the themes. I don't think any of the prepackaged themes actually give you different font colors, though, so on to plan B. Keep the "Theme Preferences" window open, and go to [http://www.gnome-look.org](http://www.gnome-look.org) or [http://art.gnome.org](http://art.gnome.org) and look for themes in the "GTK+ 2" category. When you find one you like, download the file (save it to your Desktop; don't open it directly), and then drag the file into the Theme Preferences window, and click the button to install it. You can then select the theme by name either in the main list or in the "Controls" section of "Theme Details." 

Caveat: it won't change the look of *all[i] applications; for the stubborn ones, you're pretty much short of luck. Generally, only applications that were built specifically for Gnome will be affected. That said, it will affect [i]most* applications you are likely to use.

[PS: Some applications, like gedit, Mozilla Thunderbird, and Mozilla Firefox, give you an easy way to change the fonts/colors specifically for that application. Generally, you will go to Edit->Preferences from the menu bar.]

---

### Post by matthew on 2005-09-03
[COLOR=Navy][SIZE=4]I [/COLOR][/SIZE][COLOR=DarkGreen]was[/COLOR] [COLOR=DarkRed]wondering[/COLOR] if the OP meant *[COLOR=Sienna]"How do you change colors when posting to these forums?"[/COLOR]*

While you are writing in the dialog box, look up slightly. Select the text you which to color/change size of and select what you want done from the drop down menus.

---

### Post by grofaz on 2005-09-04
Actually I have a pretty sweet custom theme I put together, adapted from the original theme I got from [http://www.gnome-look.org](http://www.gnome-look.org)  which has light blue font. This is hard to read so I want to change it to bright green. However, I can't find a way to change the font color. Nothing  about color in System -> Preferences -> Font. Is there another means ? I'm sure there must be.

---

### Post by matthew on 2005-09-04
I assume you mean the color of the font in the title bar of various windows as well as in menus and so on? This is controlled by the theme itself. You can mix and match some of the parts of various themes in System->Preferences->Theme->Theme_Details and then choose different controls and/or window borders. I do not know of a way to change the font color otherwise. If you made the custom theme, then you will need to edit it in the theme. If you didn't, then I would just have to suggest looking for a theme that has color choices you find more readable. Sorry.

---

### Post by Lux Perpetua on 2005-09-04
[QUOTE=grofaz]Actually I have a pretty sweet custom theme I put together, adapted from the original theme I got from [http://www.gnome-look.org](http://www.gnome-look.org)  which has light blue font. This is hard to read so I want to change it to bright green. However, I can't find a way to change the font color. Nothing  about color in System -> Preferences -> Font. Is there another means ? I'm sure there must be.[/QUOTE]
I see. Yes, there's a way, and it's not hard, but you will need to "get your hands dirty," as it were. 

**1. For the fonts in the body of applications:**
You'll need to modify the GTK theme itself. Navigate to <your home directory>/.themes. in the file manager or a terminal. This directory contains all the themes you've installed through Theme Preferences. Navigate to the directory of the theme you want to modify. It should have a subdirectory directory called gtk-2.0, which has a text file called gtkrc. Open this file for editing. (You should probably rename or back up the theme or somehow make a note that it's a hacked theme just to keep track of things.) I take it you've never done this before, so I suggest reading through [http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes](http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes), which is a very short intro to gtkrc files but may give you enough to start hacking. Basically, look for lines like 
```
fg[...] = ...
``` or ```
text[...] = ...
``` and set them to the colors you want. You can use the color picker in Gimp to determine the html code for the colors you want. 

**2. For the font in the window titles:**
You'll need to modify the Metacity theme itself. Navigate to the theme's main folder as in the previous paragraph and then to the metacity-1 folder. You'll need to hack the metacity-theme-1.xml file. I don't know too much about this, but here is some info: [http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes](http://live.gnome.org/GnomeArt_2fTutorials_2fGtkThemes). Or just start fiddling around  ;-)

---

