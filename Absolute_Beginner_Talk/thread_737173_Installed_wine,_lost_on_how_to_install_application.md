---
title: "Installed wine, lost on how to install applications"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Michl on 2008-03-27
I installed wine, but I can't get directions on how to
install applications.  There's alot on installing wine and
uninstalling programs, but little on installing programs.
Do I first need to install a windows OS under wine?  
There is an iexplore.exe in the virtual c:/Program Files,
but I only get an empty window, not internet explorer.
Not that I want internet explorer, but I figure if I can't
get that to work, nothing else will work for me either.

THANK YOU!!

---

### Post by Kimm on 2008-03-27
It should just as simple as downloading an *.exe and double-clicking it :)

If that doesn't work, right click on it and select "Open With Wine" If you are using GNOME, KDE or XFCE you should get a menu item for the installed application too :)

Edit:
If wine is installed you dont need to install anything extra to make it work (so no Windows OS). The iexplore.exe is not Internet Explorer (no MS software comes bundled with Wine), it is probably the Wine shell (for Status icons ans such), or a small app designed to emulate internet explorer when applications call for it (in that case iexplore.exe calls some other application).

---

### Post by TeoBigusGeekus on 2008-03-27
If you have a window$ installer, say winprogramsetup.exe, right click it and select open with Wine Windows Emulator. The software will be installed and then you can go to Applications->Wine->Programs and run your program.

---

### Post by Michl on 2008-03-27
Thanks!  The internet explorer exe file was misleading but it
is just used as a shell as noted above.

---

### Post by SlappyPappy on 2008-04-08
If you want to install IE check this out.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Just be sure to install the cab extractor first. It works great.

---

### Post by Northsider on 2008-04-08
You can also go to the console, switch to the wine directory and run "wine windowsprogram.exe"

---

