---
title: "[SOLVED] Startup script problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mbc2008 on 2008-03-04
Hi All

I am new to Ubuntu/Linux (totally awesome OS by the way) and need help.

I have installed Ubuntu on my iMac and needed something to lower the screen brightness.  I managed to find a program and am now trying to run in as a startup script but I have a few problems.

I have it in the /etc/init.d directory and have also added it to sessions but at reboot it does nothing also I can manually run it but it keeps asking for a password in terminal.

The actual application is in /home/mbc2000/OtherBacklight/backlight

I don't want to enter a password in the script for obvious reasons.

Here is the script 

#!/bin/sh

cd
cd OtherBacklight
sudo ./backlight 3
exit

Appreciate any help/suggestions.  Many Thanks

---

### Post by kpkeerthi on 2008-03-04
Open a terminal and run these commands...

1. sudo mv /home/mbc2000/OtherBacklight/backlight /usr/local/bin
2. sudo chmod u+x /usr/local/bin/backlight
3. gksudo gedit /etc/rc.local
4. Add```
/usr/local/bin/backlight 3
``` to the file. 
5. Save and Exit. 
6. Reboot.

EDIT: I'm not sure if backlight would work by invoking it from rc.local as there would be no X when it runs.

---

### Post by mbc2008 on 2008-03-04
Thank you so much, it worked perfectly.

If you have time I would like to learn and would appreciate if you could correct if I ve got it wrong so here goes.

Line 1 moves the file backlight to /usr/local/bin
Line 2 Sets permission and executes
Line 3 lets you edit the file but I'm not sure what gk before sudo is?
Line 4 file location

I'm not sure why it has to be in /usr/local/bin and what is rc.local

1. sudo mv /home/mbc2000/OtherBacklight/backlight /usr/local/bin
2. sudo chmod u+x /usr/local/bin/backlight
3. gksudo gedit /etc/rc.local
4. Add
Code:

/usr/local/bin/backlight 3

to the file.
5. Save and Exit.
6. Reboot.

---

### Post by kpkeerthi on 2008-03-04
Line 1 moves the file backlight to /usr/local/bin
[COLOR="Blue"]-Yes[/COLOR]

Line 2 Sets permission and executes
[COLOR="Blue"]- Sets permission to execute[/COLOR]

Line 3 lets you edit the file but I'm not sure what gk before sudo is?
[COLOR="Blue"]- You use gksudo to launch and run 'graphical' apps. For more info see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[/COLOR]

Line 4 file location
[COLOR="Blue"]-Yes[/COLOR]

The commands in rc.local is run (with super user privileges) when the system initializes
I prefer to keep home-grown scripts in /usr/local/bin to keep things organized. For more information see [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by mbc2008 on 2008-03-04
Thanks for all your help, I appreciate the explanation. I've been on the net for ages trying to get the script working.  Your method is easy to follow, I need to do a lot of reading now to improve my Linux skills :( Anyway thanks for the quick reply.  All the best.

---

