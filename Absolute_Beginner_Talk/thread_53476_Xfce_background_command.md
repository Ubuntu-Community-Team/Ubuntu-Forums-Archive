---
title: "Xfce background command"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by Funktown on 2005-08-01
Does anyone know the terminal command to change xfce background? I want to make a cron that'll run this command and switch backgrounds for me from a certain folder. I've been looking all over and can't really find anything on it. I'm extremely new to ubuntu, so sorry if I botched some of the lingo =P

Thanks in advance.

(Oh, and please don't tell me how to set up everything, just the command. I want to do this myself with as little help as possible.. makes learning more fun =P)

---

### Post by dave9191 on 2005-08-01
Hey, 

> 
XFbd

XFbd is a backdrop manager that displays image files on the root window, as a wallpaper (if XFce has been linked against IMLIB at compilation time, xfbd is able to use almost any kind of existing image format, ie png, gif, jpeg, bmp,tiff, etc. and scale them to fit the screen)

Please note that the use of xfbd avoids the use of the option "Repaint root window of workspace" in XFce setup screen and vice versa (both use the same root window...).




Thats a snippet from the xfce manual. I dont use xfce, but Im guessing that its something to do with that command. Also you can use xv (doesnt come with ubuntu) and paint any image to the root window (ie you desktop background). I think you might also be able to use xsetroot or something along those lines but dont quote me on that. 

If you install fbsetbg (comes wtih fluxbox), you should also be able to use that within xfce. 

Dave

---

