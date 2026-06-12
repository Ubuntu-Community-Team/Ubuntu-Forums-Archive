---
title: "[SOLVED] Application font confusion"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by SherpaDoug on 2006-12-04
I think I have a fundamental misunderstanding of application fonts in Linux.    I am running Dapper.  When I run gtkterm to look at some serial data it works, but the screen is very hard to read with thin white letters on a black background.  I basically have to turn the room lights off to read anything.  But when I go to the authors web site ([http://www.jls-info.com/julien/linux/](http://www.jls-info.com/julien/linux/)) there is a screenshot showing perfectly legible black on white text.  The text in the screenshot looks just like the text I get when I open a terminal window.  I can't find any way within the gtkterm gui to change the font it uses.  Is this something I need to change outside of the program? 

SherpaDoug

---

### Post by jordanmthomas on 2006-12-04
nevermind, I didn't notice you were using gtkterm not gnome-terminal

It does seem there is a way to configure the program though, using the -c switch, but I don't know..

---

### Post by jordanmthomas on 2006-12-04
It appears to be A GTK 1 application, so it could be a simple matter of editing ~/.gtkrc-1.2-gnome2

Look around at how to edit that file and see if it gets you anywhere.

---

### Post by SherpaDoug on 2006-12-05
Ah!  Pilot error as usual.  I found the font controls under /configuration/main window.... um er actually my wife found it...

Thanks anyway
SherpaDoug

---

