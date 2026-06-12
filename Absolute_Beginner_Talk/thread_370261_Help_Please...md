---
title: "Help Please.."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by truck87bp on 2007-02-25
I reconfigured the xorg.conf file for the 5 button mouse and ubuntu won't let me in to change it back...I get like this DOS looking screen , enter screen nams and PW ....whats next? how can I boot?:(

---

### Post by Maestro23 on 2007-02-25
> **truck87bp said:**
> I reconfigured the xorg.conf file for the 5 button mouse and ubuntu won't let me in to change it back...I get like this DOS looking screen , enter screen nams and PW ....whats next? how can I boot?:(

Try:

> startx

---

### Post by Henry Rayker on 2007-02-25
That "DOS looking screen" is a terminal. You can edit the file through the terminal, if you know what you did...or, if you made a backup (as I hope you did) you can replace it. If you need to edit the file, you can use nano ```
sudo nano /etc/X11/xorg.conf
``` and revert the changes you made.

---

### Post by truck87bp on 2007-02-26
thank you,  I know what I did...tried to add 5 button mouse...then it took a crap..I can fix it

---

### Post by truck87bp on 2007-02-26
I could not get any of that stuff to work :(   

I am reinstalling Ubuntu because I tried to add the 5 button mouse to the xorg.conf file and it blew up the system.

NOOBS:  Don't modify the mouse settings !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Titus A Duxass on 2007-02-26
You should have tried a "sudo dpkg-reconfigure xserver-xorg" first, that would have allowed you to reset things to a three button mouse.

---

### Post by truck87bp on 2007-02-26
Titus A Duxass A Duxass

Thanx for trying to help, but your an hour too late....ReLoaded already.......this Linux stuff is very hard to learn if you get blue screen similar to Win. Noobs like me can get lost easy.  And we don't know the commands or even where to look for them or what they do.

I'm almost 60 years old and have the patience of Jobe.  I need to to first learn how to back-up the system files so I can recover any problems i make for myself.

An Ubuntu Recovery Snap Shot feature would be nice in the boot up screen. ( Similar to win Sys recovery)

---

### Post by Titus A Duxass on 2007-02-27
Nothing wrong with doing another install if you have the time, practice makes perfect.

---

### Post by ispark on 2007-02-27
Hey, no offense, but X server is some serious stuff so don.t mess with it .

---

### Post by Titus A Duxass on 2007-02-27
You can mess with it all you want, just make a backup of the file first.

---

