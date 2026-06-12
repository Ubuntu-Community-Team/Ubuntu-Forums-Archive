---
title: "mc-os dock"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-24
how do i get that dock that sems like mac os??? i love it

---

### Post by Rabindranath on 2007-11-24
Install avant or kiba dock. Follow this guide. 

[http://ohioloco.ubuntuforums.org/showthread.php?t=602540](http://ohioloco.ubuntuforums.org/showthread.php?t=602540)

---

### Post by santiagoward2000 on 2007-11-24
There are various options you can choose. I personally love Kiba-Dock. I heard AWN is good too. I leave the links for tutorials to install these 2:
[Kiba-Dock]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba")
[AWN]("http://ubuntuforums.org/showthread.php?t=385981")
I hope this helps!

---

### Post by zabien1970 on 2007-11-24
I had a link   [http://thelinuxmovement.blogspot.com/2007/07/make-awn-look-like-mac-leopard-dock.html](http://thelinuxmovement.blogspot.com/2007/07/make-awn-look-like-mac-leopard-dock.html)
unfortunately when I tried to do it there's a part missing, maybe someone can fill in the missing piece

---

### Post by zabien1970 on 2007-11-24
Ok, sorry to jump on this thread but I just followed santiagoward2000's link for the AWN tutorial from there I went to the curved awn link, followed all the instructions to the bottom, downloaded the black theme, no errors or problems, then it says
 "To install these themes just download 'em. No extraction required Then go to themes/ add and locate the theme which you want to install."
For some reason I can't find this, am I missing something?

---

### Post by alwiap on 2007-11-24
> **zabien1970 said:**
> Ok, sorry to jump on this thread but I just followed santiagoward2000's link for the AWN tutorial from there I went to the curved awn link, followed all the instructions to the bottom, downloaded the black theme, no errors or problems, then it says
 "To install these themes just download 'em. No extraction required Then go to themes/ add and locate the theme which you want to install."
For some reason I can't find this, am I missing something?

if i'm reading your post correctly you're having trouble just installing themes?  If you by default have the files downloaded to your desktop, open up AWN preferences via 'System > Prefs > Awn Manager'; go to the 'Themes' tab; and click '+ Add', click on 'Desktop', and then the desired file can be double-clicked and added immediately.  You might have to close the dock and reopen it for the themes to take effect, and make sure you obviously have the theme you want selected in the 'Themes' tab of Awn manager.

---

### Post by zabien1970 on 2007-11-24
Thats what I thought, yet when I click on AWN manager nothing happens

---

### Post by Partyboi2 on 2007-11-24
What happens when you start awn via the terminal?
```
avant-window-navigator
```

---

### Post by zabien1970 on 2007-11-24
OK, that helped, I now have the icon bar across the bottom and under System>Preferences>awn manager it does open so I can now access the settings, will I have to enter that code everytime I want to launch this?

---

### Post by Partyboi2 on 2007-11-24
You can create a launcher for it which will appear on the desktop.
To do that, right click on the desktop and select 'create launcher'
 
Name: Windows Navigator (or what ever you want to call it)
Command: avant-window-navigator
[FONT=monospace]Comment: (add what every you want)
or
To add it to your menu list
System>Preferences>Main Menu
Under 'application' select where you want to place the launcher
eg. Accessories
Click on 'New menu'
fill out the launcher details like above.
Now it will be displayed in the menu list.
If you want the awn dock to load when desktop loads then add it to 'Sessions' Found under Preferences>Sessions

Forgot to mention you can delete the launcher that wasn't working in 'Main Menu'
[/FONT]

---

### Post by zabien1970 on 2007-11-24
OK, finally got it working, couldn't figure out what was wrong at first till I looked back, your original command was  avant-window-navigator , your next post had  avant-windows-navigator  , that s at the end of window threw me a loop, 
 I've got it up and running now though, thank you for the help

---

### Post by Partyboi2 on 2007-11-24
No problems sorry for the typo mistake, I should learn to proof read haha:lolflag:

---

