---
title: "Start GUI ?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by ww667 on 2006-03-07
Hey guys will tell you up front i have no idea about linux.
All eposure i have had is live distros.

Now i have done installing Ubuntu and every seems fine except i cant start graphic interface. 
I loged in at comand line with my login and pass now stuck on it.

i tryed start x
And
man xfce
But no luck.
Any advice what to do ? 
Thanks

---

### Post by Moebius on 2006-03-07
The command should be ```
startx
``` with no space between start and the x.

If you don't succed please state your system specs.

Best of luck

---

### Post by ww667 on 2006-03-07
OKay still no go.
PC details

CPU: 2.8 800 front side intel pentium
MB: p4s800-x
Ram: 3G
video Card: ATI Radeon 9800 pro
HDD: 200G
Room: samsung dvd/cd
have win xp pro on it and ubuntu

---

### Post by Sutekh on 2006-03-07
[QUOTE=ww667]Hey guys will tell you up front i have no idea about linux.
All eposure i have had is live distros.

Now i have done installing Ubuntu and every seems fine except i cant start graphic interface. 
I loged in at comand line with my login and pass now stuck on it.

i tryed start x
And
man xfce
But no luck.
Any advice what to do ? 
Thanks[/QUOTE]At the main installation screen did you just press 'Enter' or did you type server/expert then Enter?

If you did a server install then you didn't install a desktop environment.  Now you will have to choose one to install.   You can choose GNOME, KDE or XFCE

Have a look at this site, and click on the Desktops at the bottom for some screenies on these environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME](www.gnome.org) - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE](www.kde.org) - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
```

If you want [XFCE](xfce.org) - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
```

These commands will install the respecitve desktops with most of the basic programs you will need.

---

