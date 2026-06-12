---
title: "Adding a folder as a menu to Panel"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by GreenVoid on 2006-08-09
Is there any way to do it?
I tried it but found nothing.

---

### Post by jd65pl on 2006-08-09
If you have alacarte then you can do this type of thing, I think it is installed as standard.

To find go to:

APPS > ACCESSORIES > ALACARTE

---

### Post by GreenVoid on 2006-08-10
And then what?

There isn't 'Add menu as folder' or anything like that.

I can add menus to the panel, that's not the problem. I'd like to add an existing folder to panel, so that I can access everything in it by one click through the "everpresent" panel.

---

### Post by Beggar Su on 2006-08-10
Hi

Have you tried going to a folder and add it to bookmark. It will display your folder in the 'places' menu if that's what you're after.

---

### Post by GreenVoid on 2006-08-22
Beggar Su:
I'd like it directly on the panel, not in the Places menu.

---

### Post by reality_hunter on 2007-06-14
> **GreenVoid said:**
> Beggar Su:
I'd like it directly on the panel, not in the Places menu.

yeah I wonder about this too>.....is there a way to do this???

thanks

---

### Post by mcduck on 2007-06-14
No, that's not possible. If you want, you can add a launcher to open your directoryin file manager, but I don't think there's any way to make a browsable panel menu for directories in Gnome.

---

### Post by Nythain on 2007-06-14
hehe... there is in kde... but thats besides the point, i think what the poster is trying to accomplish is having something similar to a home icon on thier panel, that when clicked on opens up in a file manager at that location

---

### Post by mcduck on 2007-06-14
In that case it's easy. Just right-click on the panel, select 'Add to Panel', then 'Custom Launcher' (or whatever it's called).

In the launcher use the command 'nautilus ~/'. That should do it. (if it doesn't, use the full path, '/home/username' instead of '~/'). You can use any icon you want, or find the default home dir icon from /usr/share/icons.

That will open the home directory in spatial-mode nautilus, if you want browser instead (and you haven't set nautilus to always use browser mode), I believe there was some coption for the command, could have been '-browser' but you can always check that from Nautilus manual ('man nautilus' in a terminal)

---

### Post by GreenVoid on 2007-06-18
As Nythain said there is an applet in KDE.
But I couldn't find it in Gnome.
Thanx anyway, everyone.

---

