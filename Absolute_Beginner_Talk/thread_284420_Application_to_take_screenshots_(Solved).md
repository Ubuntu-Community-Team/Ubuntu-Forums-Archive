---
title: "Application to take screenshots (Solved)"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Pablasso on 2006-10-25
One thing i really miss from MacOSX is the ability to take screenshots of partial parts of your screen with a simple key shortcut, while it may not seem to be a big deal it saves you a lot of time of cutting in gimp.

How could this be done on Gnome?

---

### Post by tonyr on 2006-10-25
The **PrntScrn** key on your keyboard should pop up the screencapture app in
both Ubuntu and Kubuntu.   The Kubuntu app gives several area selection
options.. I don't remember right now what the Ubuntu app offers.

---

### Post by TitusDalwards on 2006-10-25
you can add  Take a Screenshot aplication to gnome panel, or you can use keyboard shortcut which is under System Menu.

---

### Post by CatKiller on 2006-10-25
It depends what you mean by partial parts of the screen. You can use Alt-Print Screen to take a screen grab of the current window. That might be what you want.

---

### Post by Pablasso on 2006-10-25
with the print key just pops a menu to save the full screen, i can take an screen also with alt+print from the current window, but what i want is to take any location of the screen, in Mac you select your choice with the pointer and the screenshot is taken, i think there are similar apps for windows too

thanks for your replies

---

### Post by Pelekophori on 2006-10-25
This article from Linux.com might be useful.  

[How to choose the right screenshot program]("http://www.linux.com/article.pl?sid=06/10/12/1843204")

---

### Post by Irony on 2006-10-25
You could use xvidcap, this is a movie video capture program, but it can do single pictures as well (you define the area to be captured in either case);

[http://sourceforge.net/project/showfiles.php?group_id=81535](http://sourceforge.net/project/showfiles.php?group_id=81535)

Simply install rc2 with the GDebi installer.

---

### Post by tonyr on 2006-10-25
[Here's]("http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux") another article with a bunch of suggestions.
Buried in it is the suggestion to use the ImageMagick command **import**
like this, for example:
```
import screenshot-name.png
```
It does require you to have ImageMagick installed, which I seem to have,
although I don't recall installing it specifically.  The behavior
is exactly as you described: A crosshair cursor appears, allowing you
to draw a rectangle anywhere in the screen with the mouse.  When released,
the selected area is drawn into the named file.  You could set up a
keyboard shortcut for this.

You can test for ImageMagick on your system by typing
```
import -version
```

---

### Post by Pablasso on 2006-10-25
thanks for all your replies, the command import from ImageMagick was exactly was i was looking for, and comes included on a default dapper installation, in fact is more versatile than the screenshooter from osx :) also xvidcap seems pretty useful too

regards

---

### Post by Pablasso on 2006-10-26
i found that scrot also has an option to select a custom area with the option -s :)

---

