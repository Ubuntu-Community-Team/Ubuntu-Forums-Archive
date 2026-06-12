---
title: "Where are the Programs installed by Automatix???"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by ervyxx on 2006-12-23
Hi!

I just installed:

1. Archiving Tools; and
2. Checkgmail

using Automatix2.

However, I don't find the icons in the menu. Where do I find the above installed proggies and why didn't they appear in the menu.

Every other proggie, installed by me using Synaptics has appeared in the menu?

Confused pals. what do i do?

---

### Post by ervyxx on 2006-12-23
HELP! Anyone?

---

### Post by dawg on 2006-12-23
cant you just run, the program name in konsole/terminal?  not sure if the debian menu deal does it or not(should also be on automatix).  have you tried editing your menu system to add apps?

---

### Post by ervyxx on 2006-12-23
If I have to run apps manually from Terminal, what is automatic then?

checkgmail ran from terminal but, it shuts down as soon as I close the terminal window

I think I better stop using Automatix

Also, it didn't download the crypt::simple dependencies and is storing my passwords in plain text.

---

### Post by dawg on 2006-12-24
well, the point of using automatix is to set up a box automatically without having to worry about looking up dependancies and what not.  have you tried editing your start/gnome menu to include those apps?  as far as the crypt password stuff goes, i've never messed with it so i don't know how to fix that.  btw i haven't ran ubuntu in some time, i usually use xp,   then mepis   then suse.  so excuse me, if some of my info is incorrect.

---

### Post by Azakus on 2006-12-24
The problem with Automatix is that it doesn't install with packages, just puts the file in place. Try using the "locate" tool to see where the programs are by name. Example:
```
locate {programname}
```Remove the {} of course.

---

### Post by michaeljustman on 2006-12-24
You can start checkgmail when you log in by adding it to your session startup under:

System > Preferences > Sessions > Startup Programs

by clicking Add and typing "checkgmail" in the box and clicking okay.

Also, alternatively to just run the program:

Press ALT+F2 and type "checkgmail" in the box to run it once.

(To run it in the terminal w/o closing with the terminal just type:
```
checkgmail &
```

This'll work with any command I think.

---

### Post by ervyxx on 2006-12-24
Seems like Synaptics is better for a newbie like me.

Thanks dawg, Azakus & michael for the tips.

Just uninstalled everything using Automatix and installed the same using Synaptics.

Still nowhere - checkgmail ???

---

### Post by LDRoamer on 2006-12-24
You can add stuff to your menus through system -> preferences -> menu layout.  If you click in the left pane on the group where you want to add the menu item it will show you what is installed in the group. I added Checkgmail to my internet Group. On the right side I just picked new item browsed to the application I wanted to add selected my preferences and that was about it. I now select it from the main menu when I want it to run.  I opted not to save the password and just enter it every time I run the application.  I don't use it all the time so this works for me.

---

