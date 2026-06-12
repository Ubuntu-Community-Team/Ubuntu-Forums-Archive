---
title: "How do I add a program to startup"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-03-13
In Gnome you can click: System / Preferences / Sessions / Startup Programs and enter a daemon to your list of start up programs. I am using KDE and my menu isn't set up like that. How do I do it?

---

### Post by bruenig on 2007-03-13
I don't use kde but I did once. I remember that there was some hidden directory in the home folder that held the autostart scripts if that helps.

---

### Post by gangrelsurf on 2007-03-13
have you tried puting a command forit in your .xinitrc file? That's the old skool way of doing it, don't know if that file gets read or not using kde though. If you try it, the file should look like this:
<code>
#!/bin/bash

command &
</code>

where the first line tells the shell to read it, then 'command' is the command you want to run, and the '&' puts it in the background and continues with your boot up.  Like I said, don't know if this will work under kde, but cant hurt, unless you forget the '&' ; )

---

### Post by tjcannon on 2007-03-30
Given that this was posted two weeks ago, I'm sure you've already figured it out.  However, for anyone who wants a simple way to do this in KDE, simply use the following menus...

K | Settings | KDE Components | Autostart Application

If you are having trouble finding the command for the program you want to run and it is already on the K menu (I don't want to call it the Start menu.  What is the name of it in Linux?), you can right-click and "Put Into Run Dialog."  Now just highlight and copy all the text and paste it when the Autostart adder asks for the command.

---

