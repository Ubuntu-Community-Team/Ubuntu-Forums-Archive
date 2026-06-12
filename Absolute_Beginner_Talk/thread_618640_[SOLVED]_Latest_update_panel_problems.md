---
title: "[SOLVED] Latest update panel problems"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by 34.50 on 2007-11-20
I booted into Gutsy today, and it said new software updates, so I hit install updates. Now, I restarted because I had to do something in Win. XP, and now booted back into Gutsy, and the Panels at the top and bottom won't start. In Windows, this would be equivalent to the "explorer.exe" process where if you close this process, you lose your taskbar at the bottom of the screen and your desktop icons. 

Any ideas on how to get the panels to work or to revert the updates? 

TIA

---

### Post by schorsch on 2007-11-20
What happens if you open the "Run Application" via ALT-F2, type "gnome-panel" and click on "Run"? Or you can start "gnome-terminal" via "Run Application" and type "gnome-panel" in the terminal; this will provide helpful output if nothing happens.

---

### Post by 34.50 on 2007-11-20
[IMG]http://i44.photobucket.com/albums/f33/tsupersonic/error.png[/IMG]

Above is the error message I get when I logon. No panels appear after clicking OK...

Anyone?

---

### Post by 34.50 on 2007-11-20
> **schorsch said:**
> What happens if you open the "Run Application" via ALT-F2, type "gnome-panel" and click on "Run"? Or you can start "gnome-terminal" via "Run Application" and type "gnome-panel" in the terminal; this will provide helpful output if nothing happens.Alt-F2 does nothing... but if I go into terminal (I have a desktop shortcut) and type in "gnome--panel" I get the same error message as the picture I've attached.

---

### Post by schorsch on 2007-11-20
Is bonobo-activation-server running? Please type
```
ps -ef | grep bonobo
``` in a terminal session and post the output.

---

### Post by 34.50 on 2007-11-21
Sorry for not getting back earlier...

Here's the output: 
ku        5863     1  0 10:35 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
ku        6024  5984  0 10:36 pts/0    00:00:00 grep bonobo

I appreciate your help :) If Bonobo activation server hasn't started, how do I go about starting it or what do I need to get back my panles? Thanks again :)

---

### Post by 34.50 on 2007-11-21
I have Xfce installed and forgot about it. I logged in using xfce, and had access to the synaptics package manager. I went to history, found the updates and marked them for reinstallation. It did its thing, and I logged into Gnome, and everything is working right. 

I appreciate all your help schorsh :)

---

