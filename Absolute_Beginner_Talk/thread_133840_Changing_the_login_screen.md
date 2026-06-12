---
title: "Changing the login screen"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-20
Is it possible to change/customize the Ubuntu (Gnome) login screen? I tried searching this several times to no avail. I imagine theres got to be a tutorial arround here somewhere for it, I just can't find it.

---

### Post by gord on 2006-02-20
id suggest taking a look at [http://gnome-look.org](http://gnome-look.org), they have lots of diffirent logon screens on there. also check out System -> administration -> logon screen setup

:)

---

### Post by Madpilot on 2006-02-20
[http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_LOGIN_SPLASH](http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_LOGIN_SPLASH).

This is actually a whole page of eyecandy tutorials - quite cool.

---

### Post by patrick295767 on 2006-02-21
[QUOTE=darkbullet87]Is it possible to change/customize the Ubuntu (Gnome) login screen? I tried searching this several times to no avail. I imagine theres got to be a tutorial arround here somewhere for it, I just can't find it.[/QUOTE]
  
I guess u meant : ```
sudo gdmsetup
```
if you installed gdm (login manager)...
I prefer thsi one much better than kdm, 'cos with 
gedit /etc/gdm/gdm.conf
u can customize a lot of things
  
U wanna change it : 
Go to [http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)
and download the file
(do not unpack it)
and with gdmsetup, u may select the one u like

Let us know if you managed to change ur login manager $

Greetings, 

Patrick
-------------
gdm stuffs :
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

