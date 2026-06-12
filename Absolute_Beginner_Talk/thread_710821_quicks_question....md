---
title: "quicks question..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by niko123 on 2008-02-28
hey guys....im using the gusty 7.10 and i have a few quick questions

1-- how would i put the file system...CD-DVD drive...and the computer icon on my desktop....

when i drag and drop....they end up having a little lock the icon...?? 

and

2--how can i change the little Ubuntu menu icon to a customize Ubuntu icon?


please help...

thanks alot in advance.!

---

### Post by sumguy231 on 2008-02-28
To put any thing in places as a shortcut on your desktop I know you can right-click on the desktop, make a launcher (type 'location') and where it says location just copy and paste the location from Nautilus when you open it from the Places menu.

To change the icon you just have to replace the icon file but I don't remember where it is at the moment. I'll go look.

---

### Post by dedmonds on 2008-02-28
You can add an icon to the desktop by right-clicking on the desktop and selecting "Create Launcher...", You can have the icon point to a directory location like your home folder by setting Type to Location, giving the icon a  name, and adding the directory path (like /home/dedmonds) to Command. You can also choose the icon image used by clicking on the icon box on the left side of the dialog box.

---

### Post by dedmonds on 2008-02-28
forgot to attach this...

---

### Post by sumguy231 on 2008-02-28
To be more specific than my last post if you want 'Computer' then put computer:/// for the location, for CD-DVD Burner, put burner:///, etc. There are special locations for them which you can figure out by opening them in Nautilus and then looking at the location bar.

---

### Post by ryanhaigh on 2008-02-28
You can open gconf-editor (alt-f2 and type gconf-editor) then search for show computer and show volumes, tick the associated boxes and you should have them on your desktop.

As far as the icon goes you can use a different icon theme, you could also try and find the actual picture that is used (it will be in /usr/share/ somewhere and probably a png image). You can then just replace this with the one you want, but you will need to run the file manager in administrator mode, once you find the location of the icon, press alt-f2 again and enter gksudo nautilus browse to the location and replace the file.

---

