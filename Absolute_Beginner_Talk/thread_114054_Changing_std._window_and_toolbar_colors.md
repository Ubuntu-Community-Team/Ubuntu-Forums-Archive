---
title: "Changing std. window and toolbar colors?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Harimwakairi on 2006-01-07
I recently customized the look of my Ubuntu installation with some stuff from gnome-look.org, including a metacity theme that changed the borders of my windows.  Now instead of being that drab grey and brown that comes standard, they're a bright, shiny white.  

My problem now is that certain apps have not changed the color of their toolbars and basic controls.  The flle explorer (nautilus?) has altered itself to look color-coordinated, but gedit and firestarter have not. 

I'm using a set of theme elements, so there's one for the login screen, one for the window borders, and one for controls, all of which are selected in my themes app.  Is there anything I might be missing?

---

### Post by ubuntuuser on 2006-01-07
This happens when you start certain apps as a different user. For example, when you start Firestarter you have to start it as root. Now it uses all settings from the root account for this program. To make these progs appear exactly like all your other apps you need to set the same theme and icons and stuff for your root account. just login as root and change the settings, then logout and restart X to see everything in the same theme.

Hope this helps.

---

### Post by daki on 2006-01-07
I think the problem might be that when you installed the theme, you might have installed it to your home directory's .theme folder.  This would affect your files, but when you use an app like firestarter, and it runs as root, it looks for the theme in /usr/share/themes, and since it can't find it, it reverts to the default theme, which is inconsistent.  The way I've solved this in the past is extracting the folder unto the /usr/share/themes folder, that way it's more of a global theme.  But... I don't know why gedit would look weird.  Hmmm.  Try this out, and see if it helps though, atleast firestarter will look better.

---

### Post by Harimwakairi on 2006-01-07
Thanks for the help.  You guys were right, it was the root user problem.  I copied the theme folders in my user account's .themes folder into /usr/share/themes and now everything is working.  As it turns out, the reason gedit looked bad is that I just installed and so am using it almost exclusively to edit configuration files (hence it's almost always preceded by sudo and therefore run as root).  

One question, ubuntuuser: you mention logging in as root, but isn't this impossible?  I thought I read somewhere in the docs that Ubuntu does not allow the root user to log in and therefore you must do everything rootish through sudo.

---

