---
title: "Only X-mouse showing when booting X (Ubuntu Server)"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by rompeldunk on 2006-12-06
Hi everyone!

Welcome the freshsmelling noobie.. :tongue: . I beg please don't slaughter me if I've missed some rule or search result that would lead to the solution to this problem. I assume it is an easy bug to fix, but I've been searching for an hour now pretty hopelessly without any clue..

I've installed Ubuntu Server Edgy, and in with it a X-desktop environment, and an automatically installation of nVidia drivers that worked perfectly.

Symptom: When i boot I get a totally black screen with the mouse pointer in an x-figure. I'm able to move it, but nothing else happends. I need to log in with Ctrl+Alt+F1, rm -rf /tmp/.X0-somename, and startx to be able to get onto the desktop.

Maybe cause:
The last thing I did was to trying to edit sources.list in pico terminal. After about 10-15 sek of holding down backspace to delete the text(yes, I haven't learned any other method to delete text in pico yet... :green: ) the computer froze totally. This is the first time this have occurred with total freezen on this server. I then made a manually power-off with the front panel switch, and the startup X-desktop fails.

Another thing I did before the freezing, was to edit the logon screen theme and some other settings there for remote login. I would assume this caused it all, but I've set these values back to the previously settings, of what I can remember at least..

I've also reinstalled the nVidia drivers from Applications --> Add/remover.., with first deleting the drivers of cource in terminal. Now my nvidia-drivers don't work either. 
I do not have the same options as before for shutdown when logged on to my personal user.

Any Idea of how I fix this? Or do I have to reinstall the desktop environment for the server? Additionally, how?

Maybe I wrote this unnecessary long. Anyways please criticize me for my writing, so I can get better. Sorry for my terrible English btw...

---

### Post by lemonsCC on 2006-12-06
OMG...you fool!  Way to hose your system :mrgreen: :twisted: :mrgreen: 

Kidding of course!

First lesson always make backups, BEFORE EDITING! To back up your sources.list you would have typed: ```
sudo cp /etc/X11/source.list /etc/X11/sources.list_backup
```

Now to fix the issue...press Control + Alt + F1, log in and type ```
sudo dpkg-reconfigure  xserver-xorg
``` and follow the questions.  If that doesn't work post back.

EDIT:  If this does work please, please make a backup of your sources.list in case you decide to go backspace crazy again \\:D/

---

### Post by lemonsCC on 2006-12-06
Any luck?  just wanted to make sure all went well...

---

