---
title: "Mouse Themes?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-03
Is it possible to get new mouse themes? If so how do you install them?

---

### Post by NESFreak on 2006-10-03
arent they living in  /usr/X11/lib/X11/icons/ ? (not sure)

[http://www.gnome-look.org/index.php?xcontentmode=36](http://www.gnome-look.org/index.php?xcontentmode=36) a collection of teams

NESFreak

---

### Post by Dinerty on 2006-10-03
```
sudo apt-get install gcursor
```

then you can download mouse themes from

[http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=2868fdd796e769948f71e69df758c527](http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=2868fdd796e769948f71e69df758c527)

---

### Post by jaboua on 2006-10-03
here are some cursor themes:
[http://www.kde-look.org/index.php?xcontentmode=36](http://www.kde-look.org/index.php?xcontentmode=36)
[http://www.gnome-look.org/index.php?xcontentmode=36](http://www.gnome-look.org/index.php?xcontentmode=36)

In KDE, go to System Settings -> Mouse -> "Cursor Theme" tab
There you can install new themes and change cursor theme.

In gnome, you can change it in System -> Preferences -> Mouse -> Cursor tab (if I remember correctly). I'm not sure how to install in gnome though. For system-wide cursors, you will have to save the cursors in /usr/X11R6/lib/X11/icons/ and edit the file /usr/X11R6/lib/X11/icons/default/index.theme

---

### Post by spyker3292 on 2006-10-03
> **Dinerty said:**
> ```
sudo apt-get install gcursor
```

then you can download mouse themes from

[http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=2868fdd796e769948f71e69df758c527](http://www.gnome-look.org/index.php?xcontentmode=36&PHPSESSID=2868fdd796e769948f71e69df758c527)

When I do that it just extracts the files.

---

### Post by spyker3292 on 2006-10-03
So how should I use it?

---

### Post by bigken on 2006-10-03
system/preferences/theme just drag and drop the file there

---

### Post by Dinerty on 2006-10-03
> **spyker3292 said:**
> So how should I use it?

sorry mate, can either drag or drop or click the install theme button on "Cursor selection"

---

### Post by spyker3292 on 2006-10-03
What kind of file. I click install and chose the tar.bz2 file and it just 
extracts the files into a folder.

---

### Post by bigken on 2006-10-03
go to system/preferences/ click on theme just drag and drop the tar.bz2 there :rolleyes:

---

### Post by spyker3292 on 2006-10-03
> **bigken said:**
> go to system/preferences/ click on theme just drag and drop the tar.bz2 there :rolleyes:

Then it just uses it as an icon theme. I trying to do Mouse Pointers on Dapper(if that makes any diff).

---

### Post by Dinerty on 2006-10-03
Try and unrar the file first onto your desktop and see if there is a readme inside or something which may tell you what to do.

You may be required to install it another way.

---

### Post by bigken on 2006-10-03
> **spyker3292 said:**
> Then it just uses it as an icon theme. I trying to do Mouse Pointers on Dapper(if that makes any diff).

yep you got it and then go to system/preferences cursor selection ;)

---

### Post by spyker3292 on 2006-10-03
Still can't get it. :(

---

### Post by Dinerty on 2006-10-03
What mouse theme are you trying to install (Put link here) and what seems to be happening when you try to install it?

---

### Post by spyker3292 on 2006-10-03
[http://www.gnome-look.org/content/show.php?content=27913](http://www.gnome-look.org/content/show.php?content=27913)

It just extracts it into a folder on my desktop.

---

### Post by Dinerty on 2006-10-03
According to the installation guide it says extract the folders to .icons, a example of this would be:

```
cp -R '/home/spyker3292/Desktop/PolarCursorTheme-Green' '/home/spyker3292/Desktop/PolarCursorTheme-Blue' '/home/spyker3292/Desktop/PolarCursorTheme' /home/spyker3292/.icons

```

Replace spyker3292 with your username :)

You may need to restart X (ctrl + alt + backspace) then go to your "cursor selection" program and it should be in there

---

### Post by spyker3292 on 2006-10-03
Worked!

---

### Post by Dinerty on 2006-10-03
> **spyker3292 said:**
> Worked!

Excellent

/me gives himself a Beer

---

