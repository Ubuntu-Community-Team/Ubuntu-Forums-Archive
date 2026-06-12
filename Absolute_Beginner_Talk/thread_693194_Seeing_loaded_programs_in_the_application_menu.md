---
title: "Seeing loaded programs in the application menu?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by USarge on 2008-02-10
New here, so be gentile...:-P

Why, after I install a new app, don't I see it on any of the menus on the panel?  For instance, I loaded clamAV and I don't see it under any of the Applications menus or System, etc?

I guess my basic question is this:
In Windows, you can go to the program folder and find the appropriate folder with the executable to launch a program.  How do you do this, in essence, in Ubuntu?

I guess there's something with the file system structure of Linux/Unix that I'm not understanding.

Thanks.

---

### Post by Xavieran on 2008-02-10
First try typing clamav into a terminal to see if it has installed correctly...
There is no real reason why it should not but this will also give you the command to put into a menu item...

If it executes press Ctrl+Alt+C to exit it and then right click on the Applications menu and select edit menus...

Go to the Category you want to put your new launcher in and click on New Item...

Fill in the command (clamav) and the name and comment if you want...
For the icon you could look in /usr/share/icons for the clamav icon....

Hope this jumbled collection of info helps :)

P.S...Most commands to start apps are the name of the application in lowercase,and are stored in /usr/bin ...

---

