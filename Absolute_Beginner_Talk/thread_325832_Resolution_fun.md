---
title: "Resolution fun"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by morebewon on 2006-12-26
During intallation on several Ubuntu 6.06 sets some have happy clear graphics at 1280/768 and a couple have become really dot-matrix looking on TFT screens w/.26 dot pitch.  Is there a means outside of the desktop menus to try out screen resolutions? 

I think I have exhausted the existing menus and, apparantly, I got a chance to select during oem installation and now I'm trapped...  somehow, I don't think it's Ubuntu, I think it's me  ;}  But where is the magic button?

---

### Post by steve.horsley on 2006-12-26
From the command line, 
sudo dpkg-reconfigure xserver-xorg
and anomgst the questions is an opportunity to list the resolutions you like.
You can switch between them while in the GUI with Ctrl-Alt-KeypadPlus and Ctrl-Alt-KeypadMinus

---

### Post by morebewon on 2006-12-26
Ya know, I just tried the ctrl-alt-+ switch for s&g and switched fonts!
So it might be a font - selection rather than an resolution thing after all.

But Thanks!

---

