---
title: "vnc remote desktop..."
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-06-24
Hi, I have one laptop and one desktop both with ubuntu dapper, i connect to the desktop via vnc.  the desktop does not have a monitor, how do i get ubuntu to not default to 640x480 resolution when no monitor is connected?  as soon as i connect one that goes to 1024x768.  ubuntu is impossible to use with such low resolution as the menus out stretch the screen etc.

thanks

simon

---

### Post by scxtt on 2006-06-24
start a server on the desktop w/ a command like this:
[indent]$:> vncserver -geometry 1154x864 -depth 24[/indent]

---

### Post by cowley on 2006-06-24
no luck  - its still 640x480

thanks

simon

---

### Post by cowley on 2006-06-25
i am still at a loss - it seems that if you start ubuntu without a monitor connected it defaults to a 640x480 resolution - despite what the xorg says.  is there somewhere else i need to edit to get it to 1024x768 whether a montior is connected or not. 

thanks

simon

---

### Post by ProjectGod on 2006-06-25
your answer

[http://www.ubuntuforums.org/showthread.php?t=172243](http://www.ubuntuforums.org/showthread.php?t=172243)

---

### Post by ProjectGod on 2006-06-25
or better straight to the source... [http://www.ubuntuforums.org/showthread.php?t=172525](http://www.ubuntuforums.org/showthread.php?t=172525)

---

### Post by scxtt on 2006-06-25
this solution might work for you cowley, but it makes no difference for my box -- my xorg.conf contains these lines as monitor definitions:```
Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 1"
EndSection
``` w/ no refresh definitions and i'm able to x11vnc [connecting to :0] into my box which is running dual screens [1600x1200 & 1280x1024] w/ no default small resolution ...

i used to have Fedora Core 4 installed on a "server" that i would VNC into - never had this problem and a monitor was only plugged into it during the install ... i could use whatever resolution i requested when starting the server ...

---

