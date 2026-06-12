---
title: "Can't boot ubuntu"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by dpar on 2006-10-27
HELP!!!! :confused:  Yesterday I was messing around with trying to get some video drivers installed, which didn't go too well. This morning Ubuntu won't boot. Gave some error regarding xorg.conf.
 Soooo, I did this from the terminal it booted into....sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
 This, I figured would restore it with the backup I made. Now I get this error.

== log file:"/var/log/xorg.o.log
== using config file: "/etc/X11/xorg.conf

Can I get back into ubuntu without a reinstall??? A reinstall won't be too much of a hardship, as I have only been using it for a couple of days.

Thanks in advance......Dave

---

### Post by Xphome on 2006-10-27
This command will start the xorg config guide:

dpkg-reconfigure xserver-xorg

when you get to the part when you can choose:

[*]bitmap

[*]glx
[ ]ddc

and many more, choose ddc(or what its called). Then reboot.

---

### Post by dpar on 2006-10-27
Thanks, xphome, for the quick reply. I'll give that a try after work tonight and let you know how it came out.


Dave

---

### Post by Xphome on 2006-10-27
np, if im not on the foruns later and the GUI(Graphical User Interface)
wont load then do the same as i told you but try the other dd- option. It worked for me after messing up the xorg.
If you have anymore questions il be on MSN (GAIM): [email]xphome62@hotmail.com[/email]   or send a email.

Simon

---

### Post by dpar on 2006-10-27
Thanks again ,xphone, I had to go through it twice for some reason, it didn't take the first time.
Back on with Ubuntu, though.:-D 
Thanks.....Dave

---

