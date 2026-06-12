---
title: "X Server Broke"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by joep on 2007-01-23
Hi I was trying to fix my screen resolution and broke it. Any help appreciated.
Error report follows

(==)log file: "/var/log/Xorg.0.log"
Time Tue Jan 23 22:14:15 2007
(==) using config file: "/etc/X11/xorg.conf"

"Depth" is not a valid keyword in this section
(EE)Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Is it possible to repair or should I start over again. I would like to repair if possible so I can learn.

---

### Post by bionnaki on 2007-01-23
open up a terminal and enter
 
> 
sudo dpkg-reconfigure xserver-xorg


---

### Post by joep on 2007-01-23
How do I do that with no screen. Sorry I'm a newbie,

---

### Post by bionnaki on 2007-01-23
you only have text? that's fine. can you get to a log in prompt? 

do this:

alt-f2 and log in
and then enter the command that I posted

---

### Post by joep on 2007-01-23
Did that
it's saying 
package xserver-org is not installed 
and no info is available

says
use dpkg --info (= dpkg-deb --info) to examine archive files, 
and dpkg --contents (= dpkg-deb --contents) to list their contens.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

---

### Post by bionnaki on 2007-01-23
well, you could always try this:

sudo apt-get remove --purge x-window-system-core
sudo apt-get install x-window-system-core

---

### Post by joep on 2007-01-23
OK.
Realized I made a typo and started over
now it's got me to 24 bit colour, I pressed OK, it says 
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20070124000530
followed by a command prompt and it doesn't seem to be doing anything.

Thanks for your helpand pardon my density.  And I am dashing between 2 PCs to do this

---

### Post by joep on 2007-01-23
Thanks for your help.  I just restarted the PC (OK I'm slow...)
I've got the screen back but it's not accepting my password.  Any ideas?

---

### Post by teitunge on 2007-01-23
First, turn off caps-lock. If that isnt working. Try logging in with root as username, and your root-passwd? Then you could manager users.

---

### Post by joep on 2007-01-23
Hi I'm the only user on this comp I ve only got one password and its not acceping it. When I enter it it flashs and goes back to the log in screen?

---

### Post by teitunge on 2007-01-23
Hm, no message which says Incorrect password?

Try to press alt+f2 and login trough the textbased window. Then you`ll find out if it is the engine, or the wrong password.

---

### Post by joep on 2007-01-23
Yes i get am incorrect password. But its the one I ve alway used. The screen goes blank and the cursor flashs then goes back to log in

---

