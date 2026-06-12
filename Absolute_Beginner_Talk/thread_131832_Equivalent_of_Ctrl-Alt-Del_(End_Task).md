---
title: "Equivalent of Ctrl-Alt-Del (End Task)"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-17
Since it's near the weekend I'll be devoting considerable time to tweaking...which means peppering this forum with rudimentary questions.  First one:  What's Ubuntu's equivalent of Ctrl-Alt-Del (End Task)?  Second one:  I'm logged in as root, yet when I try to access hidden folders it says I am not the owner of those folders.  I thought "root" was God as far as Linux is concerned.  What am I missing?  thx

---

### Post by vijayanand_sodadasi on 2006-02-17
You can view all running process using ps command.

Open terminal and type:

```
ps -ef|grep username 
```
#replace username with your login name
Then it will display all the running process on your machine.
If you want to end any process, then you can use kill command.

```
kill pid
```
#replace pid with the process id of the process which you want to kill.  The process id can be known from the output of ps -ef|grep username command.

However, there must be an easier way to do this in Ubuntu (a GUI may be).

---

### Post by AndyCooll on 2006-02-17
Theoretically it's CTRL+ALT+ESC which brings up the system monitor. With Ubuntu quite a few people report that this doesn't work however (and I'm one of those reporting!).

There are also a number of other options you might use:

```
killall programtokill
```

This seems to work provided you know what to enter in the "programtokill" bit, eg. IIRC it's "firefox-bin" and not simply "firefox"

You could always add the "System Monitor" applet (the equivalent of the Task Manager) to your toolbar and then you'd just need to click it when required.

And equally you could add the "close rogue window" (or something like that. I'm not actually at my Linux box at the moment and exactly what it's called has gone out of my head) to your task bar. This closes an open window that isn't responding.

 :cool:

---

### Post by frodon on 2006-02-17
Try that if you want that Ctrl+Alt+Del shortcut opens the system monitor like windows does: [http://www.ubuntuforums.org/showpost.php?p=576146&postcount=7](http://www.ubuntuforums.org/showpost.php?p=576146&postcount=7)
If you want to learn more on how set a custom keyboard shortcut : [http://www.ubuntuforums.org/showthread.php?t=79560](http://www.ubuntuforums.org/showthread.php?t=79560)

---

### Post by damianubuntu on 2006-02-17
Or install it from automatix, see the sticky above.

enjoy your weekend;-)
D.

---

### Post by akudewan on 2006-02-17
I use a program called xkill to kill apps that have hung. You can apt-get install xkill. Then I made a shortcut in my panel. I simply click on it, and then click on the app that has hung.

---

### Post by frodon on 2006-02-17
xkill works really well but do not kill all the prosesses related to the apps sometimes, so it's not always the best way to kill an apps but it's so fun !  ;)

---

### Post by jobezone on 2006-02-17
"close rogue window"
Yep, it's an applet you can add to any panel.

And Ctrl+alt+Esc only works in KDE, but it's a handy feature, and would be nice to exist in Gnome.

But most times, if I try closing unresponsive windows (clicking the X button) pop-up a dialog asking if I want to kill them.

---

