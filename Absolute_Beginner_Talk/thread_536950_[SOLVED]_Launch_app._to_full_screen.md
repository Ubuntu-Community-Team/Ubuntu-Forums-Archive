---
title: "[SOLVED] Launch app. to full screen"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-08-28
Does anyone know how to force an application to launch in max (full screen) mode rather than launch in a smaller window.? 

Many thanks

Laidback

---

### Post by ThrobbingBrain66 on 2007-08-28
If you run Compiz Fusion, the easiest way is to use the Window Rules plugin under the Window Management section of CompizConfig Settings Manager

The following link will give you a guide on how to use it:
[http://forum.compiz-fusion.org/showthread.php?t=1768](http://forum.compiz-fusion.org/showthread.php?t=1768)

Before trying that, you may also want to look in Gconf to see if the app has a setting you can use to do this.

---

### Post by laidback on 2007-08-28
OK, I've found the Frostwire properties in .frostwire which has the following:-

#FrostWire properties file
#Tue Aug 21 11:53:45 BST 2007
WINDOW_Y=128
WINDOW_X=139

guess the X,Y setting sets the position of the window, no mention of size though.

Any thoughts?

---

### Post by ThrobbingBrain66 on 2007-08-28
Ok. I was playing around with that file, and this is what you need to do.

set the window_x and window_y values to 0 (zero).
Then you'll notice two values within the file called APP_HEIGHT and APP_WIDTH.  You'll want to change these values to match your resolution (1280x800 in my case). Remember to take your panels into account for the APP_HEIGHT or they will cover the window.

These two values only show up if you've previously resized the Frostwire window.  This leads me to believe that you can possibly open Frostwire, resize the window to your liking and when you close the window, it will save the size.

---

### Post by laidback on 2007-08-28
OK, I have added APP_HEIGHT and APP_WIDTH, which in my case are 1280x1024, as they are missing. Yes it works!!
Maximizing and closing the app doesn't save setting for next time.

So success, many thanks. Another piece I've learnt too.

Laidback

---

