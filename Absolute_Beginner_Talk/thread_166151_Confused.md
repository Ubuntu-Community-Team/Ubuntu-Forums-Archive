---
title: "Confused"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by checkmate110 on 2006-04-25
Greetings, I am a complete newbie to linux (first try). I am good with windows and ok with the dos command line.

I just installed ubumtu (Breezy 5.10-default) The install went ok, but when I boot I end up with a blank screen. If I ctl\alt\F3 I am prompted to enter login then password and get a command line prompt. Is this normal? How do I get to a GUI from here. Do I need to install it first? Thanks in advance for any help!

Check

---

### Post by Nano Geek on 2006-04-25
Try **Ctrl+Alt+F7**.

---

### Post by Sef on 2006-04-25
Sounds like your video didn't get set up right.  To check it, do this from the command line:

sudo dpkg-reconfigure xserver-xorg

---

### Post by checkmate110 on 2006-04-25
[QUOTE=Sef]Sounds like your video didn't get set up right.  To check it, do this from the command line:

sudo dpkg-reconfigure xserver-xorg[/QUOTE]

Thanks for the replies! 

Sef, I did the above and went thru several screens of settings (all seemed sucsessful). When I rebooted I was as in my original post. (blank screen). 

asjdfwejqrfjcvm msz34rq33, ctl+alt+f7 did not do anything. Is that suposed to load the GUI?

Thanks again, Check

---

### Post by Nikusan on 2006-04-25
[QUOTE=checkmate110]Thanks for the replies! 

Sef, I did the above and went thru several screens of settings (all seemed sucsessful). When I rebooted I was as in my original post. (blank screen). 

asjdfwejqrfjcvm msz34rq33, ctl+alt+f7 did not do anything. Is that suposed to load the GUI?

Thanks again, Check[/QUOTE]

try typing startx

---

### Post by _simon_ on 2006-04-26
Do you have an nvidia card?

---

### Post by checkmate110 on 2006-04-26
[QUOTE=Sef]Sounds like your video didn't get set up right.  To check it, do this from the command line:

sudo dpkg-reconfigure xserver-xorg[/QUOTE]

Got it installed! Indeed it was a video prob. Unsupported video card..Installed it on a machine with a Radeon 9200 without a hitch.


Thanks all, Ubuntu looks very slick, and this forum is invaluable. I'll be back!!

Check

---

### Post by az on 2006-04-26
[QUOTE=checkmate110]Got it installed! Indeed it was a video prob. Unsupported video card..Installed it on a machine with a Radeon 9200 without a hitch.


Thanks all, Ubuntu looks very slick, and this forum is invaluable. I'll be back!!

Check[/QUOTE]
If you tried breezy, would you try the dapper live cd to see if that video card is now supported?  If not, would you file a bug report please?  Post back here for help on doing that.  It would be a great help.

Unsupported cards are almost all gone....

---

