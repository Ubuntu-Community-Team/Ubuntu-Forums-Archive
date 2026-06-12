---
title: "[SOLVED] Wine Programs Icons"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Anthony M on 2008-01-19
I installed Mp3tag through wine and have the icon on my desktop. I want to create a launcher in the Applications>Sound & Video menu. I know how to create the launcher, but do not know where Wine stores the picture for the Mp3tag icon....?

Thanks!

---

### Post by cecure on 2008-01-19
The icon files should be in the program directory. 

eg ~/.wine/drive_c/Program Files/the program directory

---

### Post by Malta paul on 2008-01-19
Hi, You can create your launcher using, System>Main Menu. First create a title in  'New Menu', then create "new Item'. You can then copy the ,exe file from Places>home folder (wine is in a hidden file) so use 'Ctrl H' then go to .wine, then C drv, programe files.
Hope this helps:)

---

### Post by Anthony M on 2008-01-19
Thanks for the quick reply. I was looking in that directory; the .exe is in there. but no icon file....??

---

### Post by Anthony M on 2008-01-19
Thats the thing....I have the launcher but it just has the generic icon, not the Mp3tag icon that I want. I just dont know where to find the icon that wine uses. Attached is the icon that wine placed on my desktop. This is what i want to show in my Sound & Video launcher.

Thanks Guys!

---

### Post by cecure on 2008-01-19
Have you tried looking at the properties of the icon that wine put on your desktop to see if it shows the icon path?

---

### Post by Malta paul on 2008-01-20
The icon Mp3Tac.exe is the one that will run your program, as 'cecure' said click properties and select an icon of your choice. i.e. the thumbnail you displayed in post #5
Have fun

---

### Post by Anthony M on 2008-01-20
Thanks for the help all! The wine icons are located in ~/.local/share/icons
I found this out by dragging the desktop launcher into my gnome panel then clicking properties.

---

