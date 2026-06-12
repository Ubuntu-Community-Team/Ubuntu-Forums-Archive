---
title: "Wallpaper Files Won't Show Up in Background Manager"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-12-11
I have downloaded a few wallpaper files (jpegs) and moved them to /usr/share/wallpapers.  When I then open the background manager by right clicking on the desktop, they don't show up.  Why not??  I have looked around a little bit but found any threads on this yet.  Please help.

---

### Post by dorcssa on 2006-12-11
What about the option adding backgroud in the background manager? Once added, it will be always shows up.

---

### Post by landsg on 2006-12-11
Actually, if I just add it to background manager (i.e from Gnome-Look page) it disappears if I choose another one later.  I tried copying files from /usr/share/wallpapers to /usr/share/backgrounds, but no dice.  They don't show up.

---

### Post by mcduck on 2006-12-11
Of course you have to save the image somewhere, if you just add some pic from  web browser it will disappear when you select other one.

But the easiest way is to keep your background pics somewhere inside your home directory, make a 'pics' dir or something for them.. Then you can add them using the 'Add Wallpaper'-button in Desktop Background Preferences, or from Eye of Gnome (the default image viewer) or many other image browser apps, and they'll stay in the menu.

I'd only put pics the system directories if I had many users and I wanted everybody to have that wallpaper available. Anyway, I think you might need to log out and back again for those wallpapers to show in the Desktop Background Preferences.

---

### Post by landsg on 2006-12-11
mcduck:

Thank you, and I did create a wallpapers folder in my home directory.  However, I was just wondering why Ubuntu wouldn't recognize or see the ones I put out in /usr/share/backgrounds.  Incidentally, I also can't see any root folders through Nautilus, even after I start it with "gksudo" from the terminal.  I can see root folders through terminal, but just wondering why I can't do so from Nautilus.  Thanks in advance.

---

### Post by dorcssa on 2006-12-11
By root folder you mean that ones with starting with a point? In nautilus, you have to enable show hidden files, that's all.

---

### Post by landsg on 2006-12-11
Hmmmmm.  I have that enabled, and I am still not seeing folders such as /usr, /opt, /lib.  I would consider these my root folders.  Normally I wouldn't really want to access them, but I should be able to using gksudo.  Not happening yet.

---

### Post by landsg on 2006-12-11
Well, I'm going to add to my last comment.  Now I can see root folders.  Don't know why all of a sudden, but it is now working again as before.  Thanks for the suggestions.

---

