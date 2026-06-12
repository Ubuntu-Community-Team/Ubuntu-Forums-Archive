---
title: "login with x display??"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-03-18
I am trying to set up mythtv and my twinhan 102g and used synaptic to get mythtv now it says:

> You must run mythtv-setup as the 'mythtv' user in order to complete mythtv configuration.  Note that this program requires an X display, so you must either login to an X session as the 'mythtv' user, or otherwise arrange for that user to have access to your X display.

You must complete all four steps presented in the program.

Once you have done this, you may start the backend by executing the following command as root:

/etc/init.d/mythtv-backend start

what do I do now??
Thank you so much

---

### Post by scxtt on 2007-03-18
create a mythtv user
login (to an X session) as mythtv user

do you have X11 installed?  are you using Gnome or KDE or (?)?

creating the user will be easy and logging in will be easy too ...

then run **mythtv-setup**

---

### Post by Ubukanuba on 2007-03-18
I can say that I have no idea what x11 is or if it is installed.  How can I tell?  the guides havent worked for me I get the the install mythtv screen and select language then is asks something about frontend or LAN??

---

### Post by scxtt on 2007-03-18
i've never done it myself, no need, but i hear it's quite the undertaking --- not impossilbe, but not for the faint of heart or noob-esque ...

have you installed some flavor of ubuntu and are trying to layer MythTV ontop of it?

how are you able to login at all, from a command line or a graphical "login screen"?

X11 is just a term for graphical environment ...

---

