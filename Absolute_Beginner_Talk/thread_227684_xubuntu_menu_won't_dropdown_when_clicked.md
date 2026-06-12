---
title: "xubuntu menu won't dropdown when clicked"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-02
I've just installed Xubuntu an hour ago. When I click on the Applications Menu (aka Xfce Menu), I don't see the menu dropping down anymore. All I see is the click-impression on the icon. 

I've followed the advice in the xubuntu release notes and have deleted the ~/.config/xfce4/desktop/menu.xml and re-logged in. 

When I right click on the Applications Icon, and select Edit Menu, I see all those stuff which are in the menu.

What is wrong?

---

### Post by dolby on 2006-08-02
its a solved bug all u need is to upgrade the packages

---

### Post by hanzj on 2006-08-02
and how do i upgrade the packages? I've just installed Xubuntu, so I don't know how to do anything in Xubuntu.

---

### Post by anaconda on 2006-08-02
If I remember correctly, deleting the menu.xml was not enough.

You have to copy a new menu.xml to its place.
There is a copy of it somewhere.. cant remember where...
use 

whereis menu.xml

on terminal to find it....

for some people it was enough to just delete it, but for others it wasn't. you can check. If after deleting the menu.xml and rebooting the NEW menu.xml is (also) empty, or a new one isn't created at all, then you must copy the working wersion from the other location...

---

### Post by eXisor on 2006-08-02
Assuming you have a working internet connection, simply select the menu, then System, then Update Manager, select check. It'll tell you what it can update. Be ready for 70mb or so of downloads.

---

### Post by hanzj on 2006-08-02
But when I left-click the menu, nothing pops up. In other words, I cannot proceed with your instructions. 

Please tell me how to do updates via Terminal.

---

### Post by anaconda on 2006-08-02
Correct the menu first..

by pressing "Ctrl-Alt-F1" to go to terminal (Ctrl-Alt-F7 to get back)

And then:

whereis menu.xml

and then copy it to where it is supposed to be

If you cand find the copy, I can check the path for you.

And the bug was that when you try to modify the menu it stopped working.

Then when you get the menu working you can update graphically .. if you prefer that..

---

### Post by hanzj on 2006-08-02
anaconda, thanks.
I'll try that when I get the box running. But in the meantime, I'd like to know how to update the computer via terminal.

---

### Post by anaconda on 2006-08-02
Cheked the path.. If you type the following in terminal you will get your menu back..

cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml

And to update via terminal:

apt-get update
apt-get upgrade

the "update" updates your apt-get according your sources list (list of addresses where the updates are searched from.)

and "upgrade" installs the updates it finds...

---

### Post by eXisor on 2006-08-02
To do it from the terminal...

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by dmeehan on 2006-08-06
same thing happened to me, thanks for the info to fix it!

---

