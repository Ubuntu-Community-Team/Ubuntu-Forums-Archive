---
title: "Changed logon theme now I can't get into GUI!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Nemo0075 on 2008-02-11
Here is what I have done, hopefully there is a way that I can undo it without having to re-install.  I decided to change the login theme and I did so without any problem until the first re-boot.  When it should get to the logon menu, I get a black screen and eventually a little window telling me that it is unable to locate logon… trying to use another until eventually just black.  If I re-boot and go into recovery mode and then use the exit command from the prompt I run into the same problem.   However, if I use the login command for the non-graphical logon it works but then how do I get back into the GUI to set the logon back to the default theme.  The only that I didn’t try was using the live CD to try and recover if that is possible?  I am not well versed at the command prompt so please be gentle.


BTW: Been using Ubuntu now for 3 months and love it, this has been my only real hiccup.  I have learned a great deal reading these forums.  Thanks for the info and help

---

### Post by lswest on 2008-02-11
you can switch to a tty screen (ctrl+alt+f1) at normal boot and log in there, then try running "startx" and see what errors exactly you get.  otherwise you can re-install gdm or install xdm or kdm temporarily

---

