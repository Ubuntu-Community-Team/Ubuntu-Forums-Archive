---
title: "changing mouse button action for one user"
date: 2006-10-25
forum: Assistive Technology &amp; Accessibility
---

### Post by mkoyle on 2006-10-25
This isn't what you normally expect here, but I am looking for an accessibility option that will allow my two year old son to use tux paint.  

Since he can't differentiate between the buttons on the mouse, he mostly clicks the left mouse button.  I tried changing the mouse to left-hand mode but this did not quite fix the problem either.

Does anyone know of a way to change mouse button actions to all be right click for just one user?  This is the computer my wife and I use at home so changing the xorg.conf file to modify it for all users would be rather inconvenient.

Thanks,

--Matthew

---

### Post by frafu on 2006-10-25
Hello, 

[This]("http://ubuntuforums.org/showthread.php?t=264372&highlight=disable+mouse+button") thread might help you. 

Maybe a hardware mouse with only one button could also be an option. 

frafu

---

### Post by mkoyle on 2006-11-08
I am still trying to find other options.  Since Tux Paint has its own option for using all of the mouse buttons as right click, my son is able to use tuxpaint.  I just added a file to his home directory ~/.tuxpaintrc and put 

nobuttondistinction=yes

on the first line.  Now he is able to use it somewhat.

--Matthew

---

