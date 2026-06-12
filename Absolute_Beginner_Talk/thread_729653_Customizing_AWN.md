---
title: "Customizing AWN"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by BluePlum on 2008-03-20
i must be blind or something. I always made[COLOR="Red"] AWN[/COLOR] 3d but i just cant find the 3d button now in the [COLOR="Red"]AWN[/COLOR] menu. How do i turn it from 2d to 3d? Thank you.

---

### Post by bigken on 2008-03-20
bar appearance/look

---

### Post by BluePlum on 2008-03-20
thx man im so dumb, cheers :D

---

### Post by bigken on 2008-03-20
:lolflag:

---

### Post by BluePlum on 2008-03-20
well actualy im dumber, I select it to start on login but it doesnt. YES IVE SELECTED IT! ill attach SH :D.

---

### Post by BluePlum on 2008-03-21
bumb

---

### Post by FreewareFan on 2008-03-21
Yeah, it didn't work for me that way either.

I had to add it to System - Preferences - Sessions - Startup Programs   to get it to start when I boot the system..

---

### Post by BluePlum on 2008-03-21
> **FreewareFan said:**
> Yeah, it didn't work for me that way either.

I had to add it to System - Preferences - Sessions - Startup Programs   to get it to start when I boot the system..

What Is the command to start it?

---

### Post by FreewareFan on 2008-03-21
Enter the following on the line where it says command:

avant-window-navigator

That will do it for ya!

FwF

---

### Post by neotasic1 on 2008-03-21
> **BluePlum said:**
> What Is the command to start it?

avant-window-navigator

You can test this beforehand by typing it in a terminal

---

### Post by BluePlum on 2008-03-21
Thx guyssssss

---

### Post by FreewareFan on 2008-03-21
You bet!!

---

### Post by BluePlum on 2008-03-22
another question  on AWN heh.... ive seen people and they have all mac icons on there bar like there applets, but i went into applets and none of it looks mac style and theres no firefox, DO they have applets on there bar or is it something else?

---

### Post by BluePlum on 2008-03-22
anyone

---

### Post by lswest on 2008-03-22
sounds like they were using the Mac OS X icon theme from
[http://gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Debian?content=74892](http://gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Debian?content=74892)

that what you were looking for?

or the mac4lin icons from
[http://www.gnome-look.org/content/show.php/Mac4Lin+Leopard+GTK+Metacity+Theme?content=68411](http://www.gnome-look.org/content/show.php/Mac4Lin+Leopard+GTK+Metacity+Theme?content=68411)

*EDIT* sorry, the actual icon pack is at [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

---

### Post by BluePlum on 2008-03-22
i do have a theme installed tho, a mac one. I just needa no how they put all that stuff on bar and made it mac looking, i guess i no the mac bit now, Just the bar part.

---

### Post by lswest on 2008-03-22
the icons should be in /home/<username>/.icons/[nameoftheme] so you can specify which icons are used for what launcher, tedious, but it would work.  If it's not in that folder, there is another icons folder, but i'm unsure of the path (in the process of replacing XP with vista on my laptop cuz of DVD playback issues and a few quirks with some apps i need for school, and then i'll be installing the Hardy Beta, so no time to check atm, might check on my PC later) but you can find it out yourself by running ```
locate icon
``` and it will give you a list (probably a long list) of folders or paths to files that have the word "icon" in it.  It should be pretty obvious (by how many times one shows up) which the other icon storage folder is.  Good Luck!

also, you might want to have a look at the end of step 8 from [http://linuxondesktop.blogspot.com/2007/12/making-your-ubuntu-look-like-mac-os-x.html](http://linuxondesktop.blogspot.com/2007/12/making-your-ubuntu-look-like-mac-os-x.html) it shows a theme for AWN.

---

