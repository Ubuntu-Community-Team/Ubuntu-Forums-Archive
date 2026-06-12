---
title: "Desktop Messed Up"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2008-04-09
I'm using Xubuntu on a laptop of mine. Its running 8.04. Today when I logged on, my wallpaper didnt appear. Also, all the icons are gone. And I cannot right click to display a menu. I restarted and still nothing. Everything was working last night when I shut down, and to my knowledge nothing has changed. Ideas?

---

### Post by buried on 2008-04-09
hmm, can you open the terminal if not then it's busted.

---

### Post by toasty_ghosty on 2008-04-09
> **buried said:**
> hmm, can you open the terminal if not then it's busted.

I can. But I like my icons....and wallpapers...

---

### Post by toasty_ghosty on 2008-04-09
I found out what was wrong. For some reason, XFCE was not managing the desktop. Could that have happened due to an update?

---

### Post by medivh on 2008-04-10
same here happened after update and restart but i am using gnome not xfce.can someone help me to fix it?

---

### Post by medivh on 2008-04-10
Ok i have solved my problem but still i dont know what changed the settings to make my icons dissapper. I just know it happened after update.

Here is what i did to restore icons.

first i run Configuration Editor with gconf-editor command.
then from leftside panel apps->nautilus->preferences

then i removed the check of show_desktop option closed the editor and run again. I rechecked the show_desktop and restarted computer. Icons are back. I hope this will work for other people also.

---

