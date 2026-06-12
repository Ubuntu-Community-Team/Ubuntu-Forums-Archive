---
title: "How do I prevent tomboy from displaying notes on startup?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-17
Right now, I have Tomboy notes set to start up at login, but everytime I log in, tomboy pops up with the window containing all my notes.  I'd rather only have the panel applet start on login and only have that window show when I call it myself.  Knotes displays the same sort of behavior--when I have it set to start on login, it automatically generates a new note on login.  How can I change it so that the note applications only start themselves in the panel without popping up new notes or windows that I didn't ask for?

---

### Post by laptoplinux on 2007-05-17
Ok, I found a solution for this one.  Instead of using the Preferences -> Sessions window to call tomboy itself at startup, I wrote a startup script for tomboy like thisL

```
#!/bin/bash
tomboy

``` 

And I called that script in the Preferences -> Sessions window.

Or, you can use the Preferences -> Sessions window and just call /usr/bin/tomboy instead of just tomboy.  I don't know what the difference is between those two commands, but that way works too.

---

### Post by crossedout on 2007-05-18
Thanks for the update laptoplinux, was wondering that myself.

-Xout

---

### Post by Limitlesschannels on 2007-05-18
how do I do this as root; i.e. without the password prompt?

---

### Post by laptoplinux on 2007-05-20
Ok, I should add an update to this.  I finally found out what my problem was, and it was a fluke that these fixes worked at all, and they only worked by accident.

My problem was that I had placed a tomboy applet in the panel, but I also called tomboy as a startup program.  Therefore, tomboy was getting called twice at startup since the panel applet always loads at startup and the startup process list calls it again.  Hence the window popping up.  If you run/execute/call tomboy when the application is already open, it pops up the "Search all notes" window.  So either put it in as a panel applet or call it from the sessions startup program list, but don't do both.  That should solve the problem.

(RESOLVED)

---

### Post by A. J. Rimmer on 2007-07-29
I have had the same problem with Tomboy.  This seems like a good fix, except...

Tomboy keeps getting put in the Sessions automatically, If I delete it, it just comes back.  If I uninstall Tomboy and then reinstall, it reappears in Sessions.

Some setting must be messed up somewhere, but I'm out of ideas as to where to look.

(Recently did a two-step upgrade from Dapper to Edgy to Feisty, which is when the trouble started.)

---

### Post by beetastic on 2008-04-09
@A.J. Rimmer
I can't reproduce this 100%, but I think that the phantom execution of tomboy is caused by the tomboy module in *deskbar-applet*.

Perhaps the "Search All Notes" window is getting launched when deskbar runs tomboy?

I worked around it by removing my tomboy applet, so when I log in, deskbar launches tomboy in the notification area.

Can anyone else reproduce this?

---

