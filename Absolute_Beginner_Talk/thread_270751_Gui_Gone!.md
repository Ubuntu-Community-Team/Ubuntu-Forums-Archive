---
title: "Gui Gone!"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Emasters on 2006-10-03
Somehow someway I managedto loose my gnome desktop environment.  When I start Ubuntu every thing seems cool but I onlt get the command prompt.  When I try to load ""sudo aptitude install ubuntu-Desktop"  I get un resolveable dependency issues and I get know where.  

How do I edit my /etc/sources.list file to see if I have all the requried repositories, for that hatter what are the reuqired repositories?  

Do I have to uninstall.  If so how do use the command prompt to save the data I have to a CD?

Where is there a list of bash commands that ubuntu supports?  Thanks in advance.

---

### Post by Brownedwg89 on 2006-10-03
did you try```
sudo gdm
```

---

### Post by sonny on 2006-10-03
When you enter to the terminal login and then write:
```
sudo /etc/init.d/gdm start
```
If that doesn't help  then write:
```
startx
```
If that doen't help that means you were playing with your xserver, if you played with it but didn't uninstall it just write:
```
sudo dpkg-reconfigure xserver-xorg
```
But if you uninstall your xserver, then you have to write:
```
sudo apt-get install xserver-xorg
```

---

### Post by sonny on 2006-10-03
If the problem is the Gnome Desktop Manager then you can reconfigure it by typing:
```
sudo dpkg-reconfigure gdm
```

or if you know you uninstall it, then install it by typing:
```
sudo apt-get install gdm
```

---

### Post by Emasters on 2006-10-03
OK when I reconfigure the X server I get a blue screen and prompt boxes etc.  However at the end it just goes back to the command prompt.  when i tyoe gdm or "aptitude install gnome-desktop" i get unresolved dependencies. 

How do I do a clean reinstall?  HELP!!!
\

---

### Post by sonny on 2006-10-03
> **Emasters said:**
> OK when I reconfigure the X server I get a blue screen and prompt boxes etc.  However at the end it just goes back to the command prompt.  when i tyoe gdm or "aptitude install gnome-desktop" i get unresolved dependencies. 

How do I do a clean reinstall?  HELP!!!
\
Try with: sudo apt-get install gdm

---

### Post by comppsyco on 2006-10-03
did you type startx after you reconfigured xserver-xorg?

---

### Post by Emasters on 2006-10-03
when I type startx I get a screen with an x for the mouse cursor in teh middle and a terminal window in the type left.  I can type commands into the terminal window but no gnome desktop.  Wehn I type "aptitude install gnome-desktop" I get unresolved dependencies.  HELP!!!

---

### Post by dolphinsonar on 2006-10-09
I had the same problem, this solution worked for my inspiron B130 Lappy running dapper.

> **sonny said:**
> If the problem is the Gnome Desktop Manager then you can reconfigure it by typing:
```
sudo dpkg-reconfigure gdm
```or if you know you uninstall it, then install it by typing:
```
sudo apt-get install gdm
```

---

