---
title: "Ctl + Alt + F12"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-05-09
I use Remote Administrator to remote control some computers.  When I am using my ubuntu box to RDP into my server, then RAdmin into other machines, i often have to hit CTL + ALT + F12 to send a CTL ALT DEL signal to log onto servers.  When I hit CTL + ALT + F12 my ubuntu crashes, i get a black screen with a blinking curser in the upper left.  I looked in System ~> Preferences ~>  Keyboard Shortcuts and could not find anything, any help would be greatly appreciated.  Thanks

---

### Post by Regel on 2007-05-09
Ctrl+Alt+F12 switches you to another X-session (or something)
You can get back by hittin Ctrl+Alt+F7

---

### Post by Tomosaur on 2007-05-09
Hit ctrl+alt+f7 to bring yourself back to the gui.

In Linux, you have virtual terminals. By default on Ubuntu, there are 6 virtual terminals running ( ctrl+alt+F1...6), and the GUI (ctrl+alt+F7). You can run alternate X servers on ctrl+alt+f8...12, but there's nothing running on them by default. Not sure if it can be done, but you could look into automatically connecting to your server on one of the 'empty' screens, and forwarding X to it. I don't know the exact details of how you would do that though.

---

### Post by BHelts on 2007-05-09
Thanks a lot for the replies, that gives me a great answer.  Is there a way to disable the F8-F12 key combos that switch to sessions that don't/can't exist?

---

### Post by BHelts on 2007-05-09
In addition, yes, i can hit CTL ALT F7 and get back to the GUI...... THANKS!!!!!

---

### Post by ilvg2k on 2007-05-16
As a work-around I am pretty sure in radmin, to send a ctrl-alt-delete you can also right click the radmin window and select "Send Ctrl-Alt-Delete..." or something to that effect....

---

