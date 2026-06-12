---
title: "Exporting themes"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-05-11
Hi, I'm training myself on Ubuntu before installing it and have learned quite a lot, I think. My question is this: how can I export a Gnome theme? This is the process I have tried:

1. Saved the theme at "Apply theme".
2. Opened File Browser, went to "themes:///"
3. Copied the file with my theme's name into the desktop.

In order to check if that works, I did the following:
4. Changed to Human theme.
5. Deleted my theme from "themes:///"
6. Opened "Apply theme"
7. **And when I Drag-and-drop the copy of my theme from the desktop, it tells me that the file format was lost**
8. Tried to copy the theme from the desktop into "themes:///" and no way.

If I try to access the copy I created, it tells me it's not a folder (!?). Afterwards, Gnome begins to fail: icons on desktop begin to be disturbed, no response to "Logout", etc... but menus work and I have to escape typing "sudo kill gdm" on Terminal... and restart Gnome from console. (Thank God that there are command lines! I've used MS-DOS for years; command lines are a powerful tool no OS should decline to have!)

Any guess what's wrong?

Maybe I'm a too exigent beginner. Actually, I really don't need to have a theme backup now, but wanted to know how to do it and began to try, as part of today's Ubuntu's autolesson which also included a successfull Adobe Flash Player 9 install from Adobe's website (Yes, I know I have Synaptic, but I wanted to learn how to use .tar files).

---

### Post by netyire on 2007-06-22
Sorry for the late reply. I stumbled upon your post, having searched the forums for something like "backup theme". I've compiled a nice OSX lookalike theme which I want to keep. Anyway, I did some thinking and heres what I think: (Sounds funny, doesn't it)

The themes:/// location may simply display the configuration files for all the themes, however, the themes:/// location may not be a real location on disk but rather, possibly a filter which displays the themes config files. **[COLOR="Green"]Thereby, although it may be possible to copy from the themes:/// , it may not be possible to write to it, as, writing is to a real location, not a filter.[/COLOR]** Furthermore, **[COLOR="Green"]copying the configuration file is not the same as copying the files described in the configuration file[/COLOR]**. Hence it is almost useless.

If you want to do it the quick and dirty way, just copy the **[COLOR="Red"].themes[/COLOR]** directory inside the user's home folder. If you want the icons, then copy the **[COLOR="Red"].icons[/COLOR] **directory, also inside the user's home folder. Thats it!

If you wish to be more specific in the themes which you wish to export, simply select the theme from the .themes directory and the components that make it up. For example if I am using a theme called custom1 with customcontrols for the controls, customicons for the icons and customborders, I would copy the custom1, customcontrols and customborders in the .themes directory and the customicons folders in the .icons directory.

Don't forget to backup the wallpaper, splash screen and login screen! The login screens are stored in the **[COLOR="Red"]/usr/share/gdm/themes[/COLOR]** directory.

To install the exported theme, simply** [COLOR="Blue"]copy the folders to their respective locations and follow the standard theme installation routine.[/COLOR]**

Again, sorry for the late reply, I only came across your post today. :D

---

