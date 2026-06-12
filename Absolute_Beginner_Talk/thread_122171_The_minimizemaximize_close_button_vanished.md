---
title: "The minimize/maximize close button vanished"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by envelope on 2006-01-26
I was trying to lighten the load of my linux and removed most packages i
dony use. On the process i found i had also removed the buttons to minimize
maximize and close buttons on the top corner of all programs

What package should I install to bring that back?

---

### Post by o_fortuna on 2006-01-26
[QUOTE=envelope]I was trying to lighten the load of my linux and removed most packages i
dony use. On the process i found i had also removed the buttons to minimize
maximize and close buttons on the top corner of all programs

What package should I install to bring that back?[/QUOTE]
I have no idea. One thing you could do is install ubuntu-desktop, which will reinstall the "base system" (ie, everything that was originally installed). Then, you can go back and uninstall stuff you don't need; although, I wouldn't recommend doing that -- it's just to easy to make a mistake, as you found out. Unless you're seriously out of Hard Drive space, I'd just keep ubuntu-desktop installed.

---

### Post by envelope on 2006-01-26
If I have to install ubuntu-desktop again. That means my whole work of removing the uneeded packages will got to waste. I know that it could be some gtk or gnome package

---

### Post by mettallicat on 2006-01-26
try change theme.... 
maby can be that theme freaking off you a bit

---

### Post by Viskovitz on 2006-03-23
[COLOR="Purple"]Hey! Maybe it's too late, but I post the solution anyway.

I did exactly the same mistake as you: removing packages in order to improve performance: WROOOONG! Ok, failing is learning. I installed them all again, but still no max/min/restore buttons. Also the "show the desktop" button on the bottom pannel didn't work. Looking for info on Gnome I discovered that it is not a window manager, as I thought, but instead it needs an external one. Soooo the package I/we erased and we shouldn't have was METACITY, the window manager. Once you have it back, execute it from terminal

~$metacity

and the problem's gone :D

Coffe is addictive, Ubuntu is coffee... Ubuntu is extremely addictive!!![/COLOR]

---

### Post by mcduck on 2006-03-23
removing packages will only save disk space, not increase performance :D

To increase performance it's better idea to try using XFCE4 or some light window manager instead of Gnome/KDE. Or install BUM and disable some services you don't need (make sure you know what you are disabling _before_ you do anything).

---

### Post by haider_up32 on 2008-03-25
same happened with me....i did not remove ANY of the packages...i only installed compiz fusion and was exploring some settings under appearance

---

### Post by haider_up32 on 2008-03-25
GOT the solution....happened coz of emerald theme manager

---

### Post by RedMartin on 2008-04-30
Sorry to bring an old-ish thread back but I also had this problem and solved it entirely differently.

It was Compiz 'show desktop' at fault. As soon as I disabled it the buttons reappeared.

---

