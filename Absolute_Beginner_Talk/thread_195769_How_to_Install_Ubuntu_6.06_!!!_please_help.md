---
title: "How to Install Ubuntu 6.06 !?!?!? please help"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2006-06-13
I am having some major problems trying to install 6.06 (Dapper).
I use the 'F' keys to set my monitor size (1024x768) and set the language but when I press 'enter' (high lighted on 'Start or Install Ubuntu') it goes through the whole process as if it was installing but when I get to the Xserver error and try to fix the xorg.conf file so that it will accept my nvidia card and then save and exit I try 'Sudo X' and nothing happens, it stays in the bash screen and when i try to restart the computer it only ever takes me back to my windows installation.


My question is...
How do I actually install Ubuntu 6.06 (dapper) onto the harddrive and completely kill the windows?
I want a full-Linux-box with no swaps or prtitions.

Thankz

---

### Post by halfvolle melk on 2006-06-13
My ATi wasn't recognised properly either. When you end up at the command-line you can edit xorg.conf or run
```
sudo dpkg-reconfigure xserver-xorg
startx
```
That should give you an Xsession that may not be all that hot, but will do for installing.

---

### Post by nitricacid on 2006-06-13
[QUOTE=halfvolle melk]My ATi wasn't recognised properly either. When you end up at the command-line you can edit xorg.conf or run
```
sudo dpkg-reconfigure xserver-xorg
startx
```
That should give you an Xsession that may not be all that hot, but will do for installing.[/QUOTE]

Well I have had Breezy installed and i know my way around setting up my nVidia card from the 'pico /etc/X11/xorg.conf' file so i can get the graphics set up down, it's just that when I try to start the Xserver to run the actual GUI (gnome) it needs to be restarted and that is when everything goes back to the begining of the install.

Anyone know if i install breezy and then use the Dapper CD if it will just update everything?

---

### Post by localzuk on 2006-06-13
Try downloading the 'alternative cd' and install from that.

---

### Post by nitricacid on 2006-06-13
WILCO, Rodger that.
I didn't even relize there was such a thing.
I am downloading now...

I will let ya know how it goes.

Thanks

---

### Post by halfvolle melk on 2006-06-13
[QUOTE=nitricacid]it's just that when I try to start the Xserver to run the actual GUI (gnome) it needs to be restarted and that is when everything goes back to the begining of the install.[/QUOTE]
You said you tried 'Sudo X'. AFAIK that's not how start X. 'startx' however ... ;)

Or you could try to dist-upgrade if startx doesn't work or you.

---

### Post by nitricacid on 2006-06-13
Just wanted to say thanks to everyone that helped.

I just installed fresh and everything seems to be in order and working great.

Thanks again :D

---

