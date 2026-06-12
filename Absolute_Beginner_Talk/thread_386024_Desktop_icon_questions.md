---
title: "Desktop icon questions"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by getut on 2007-03-16
Ok... a little on the stupid side... but I've got two questions regarding desktop icons.

1) The first one is windows apps under wine. If the app doesn't create desktop icons, I  how to create a launcher myself... but how do I get it to use the real windows icon instead of launcher "emblems"

2) Native linux shortcuts.. are emblems all there are... where are more icons stored so that items I put on the desktop are a little more distinguishable.

---

### Post by bbskeelz on 2007-03-16
Right click -> property ->  clicking on the picture will allow you to change the icons.

i think the other icons are in usr/share/icons ?  you can download some real nice ones from 

[http://www.gnome-look.org](http://www.gnome-look.org)


sc

---

### Post by buuntuu! on 2007-03-16
1. no idea, don't use wine
2. /usr/share/pixmaps
have fun

DANG! too slow!! (but our posts amend each other;))

---

### Post by mcduck on 2007-03-16
1. I can't give exact help as I'm not using wine myself, but the command for the launcher should be 'wine /path/to/your/program.exe', and I believe wine installs everything in a hidden directory inside your home dir so you should be able to find the exact path that way.

2. take a look in /usr/share/pixmaps and /usr/share/icons. Those are the places where most apps install their icons.

---

### Post by SMS on 2007-03-16
lol mcduck
like what you did with the /path/to/your/program.exe
lol (easily amused)

---

### Post by qamelian on 2007-03-16
> **getut said:**
> 1) The first one is windows apps under wine. If the app doesn't create desktop icons, I  how to create a launcher myself... but how do I get it to use the real windows icon instead of launcher "emblems"

This could be tricky. Most Windows applications don't store their icons in separate files. Although some do use .ico files that could be converted to xpm or png for use in Linux, most icons are actually embedded in the application's executable or in a DLL. WHen this is the case, you need to use an application that can extract the icon from the file in which it is embedded. Some Windows icon editors have the ability to do this extraction.

---

### Post by mcduck on 2007-03-16
> **SMS said:**
> lol mcduck
like what you did with the /path/to/your/program.exe
lol (easily amused)

Well, I'm glad that I managed to make your day a bit nicer :D

---

### Post by getut on 2007-03-16
> **qamelian said:**
> Although some do use .ico files that could be converted to xpm or png for use in Linux, most icons are actually embedded in the application's executable or in a DLL. WHen this is the case, you need to use an application that can extract the icon from the file in which it is embedded. Some Windows icon editors have the ability to do this extraction.

Ubuntu somehow does this on its own.. Take for example... If I install an application under wine and the application creates its own desktop icon for me... then I have the nice intended windows icon on the desktop. But if the installer blows up prior to creating the icons, or if I delete the icon by mistake, I can't seem to recreate it with anything except for the gnome "emblems". If it does it automatically, then it seems like there should be a method hidden to RE-do it manually hidden somewhere.

---

### Post by qamelian on 2007-03-16
> **getut said:**
> Ubuntu somehow does this on its own.. Take for example... If I install an application under wine and the application creates its own desktop icon for me... then I have the nice intended windows icon on the desktop. But if the installer blows up prior to creating the icons, or if I delete the icon by mistake, I can't seem to recreate it with anything except for the gnome "emblems". If it does it automatically, then it seems like there should be a method hidden to RE-do it manually hidden somewhere.

Weird. I've never have this happen unless a program has a separate, non-embedded graphic for its icon. Anything with the icon embedded has always just given me a generic icon.

---

