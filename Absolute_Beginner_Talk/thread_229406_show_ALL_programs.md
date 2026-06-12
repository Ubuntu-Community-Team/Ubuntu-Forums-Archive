---
title: "show ALL programs"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-04
how can I see all my installed programs ?
I don't mean packages that I see in synoptic
I have the adept , but I can choose/see it only when I press alt+F2
and that b/z I know I have this program
but I have lots of other programs that I don't know about.
how can I see them ?
I don't mean in the add/remove programs
I want to see them in tabs >applications/system

---

### Post by jd65pl on 2006-08-04
If you have alacarte menu editor,

then go to apps > accessories > alacarte.

That might help a bit

---

### Post by MaximB on 2006-08-04
> **jd65pl said:**
> If you have alacarte menu editor,

then go to apps > accessories > alacarte.

That might help a bit

yes ... but it doesn't show ALL the programs I have
I need to view ALL of them

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> how can I see all my installed programs ?
I don't mean packages that I see in synoptic
I have the adept , but I can choose/see it only when I press alt+F2
and that b/z I know I have this program
but I have lots of other programs that I don't know about.
how can I see them ?
I don't mean in the add/remove programs
I want to see them in tabs >applications/system

  
To fully see what's installed in your machine :
```
dpkg -l
```
  
Go too in /usr/bin ...

---

### Post by Tomosaur on 2006-08-04
Open a terminal, double tap the 'tab' button on your keyboard. Press y, press enter, then peruse at your leisure.

---

### Post by MaximB on 2006-08-04
yes...but I need to see them in the applications menu - so I could choose them

---

### Post by SoloSalsa on 2006-08-04
I would like the same.  Bump!

---

### Post by patrick295767 on 2006-08-04
oohh,
 
```
sudo apt-get -f -y install kicker
kicker &
```
 
Have a look the plenty apps you have !! 

Enjoy !
  
----
To install more: 
forinstance:
  
1/ ```
apt-cache search dictionary
```
look the pkgname
  
2/ then, 
```
sudo apt-get -f -y pkgnameselectedofdictionarythatlookspromising
```

---

### Post by MaximB on 2006-08-04
say - is that KDE looks like ???

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> say - is that KDE looks like ???
 
(kicker is one part of kde)
You dont need kde to have it: [http://patrick295767.sitesled.com/fvwm/desktoppatrick.jpg](http://patrick295767.sitesled.com/fvwm/desktoppatrick.jpg)
 for an fvwm desktop.
  
You can do anythg you want with linux, that's very great, isnt it?
  
And example : 
```
sudo apt-get -f -y install gnome-panel kicker
gnome-panel & kicker & 
```
You see ?

---

### Post by MaximB on 2006-08-04
this sh*t is great
but I don't like KDE
it's really like winxp...
by the way - somehow my problem has been solved with gnome
now I can see the debian menu (don't know what I did).

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> this sh*t is great
but I don't like KDE
it's really like winxp...
by the way - somehow my problem has been solved with gnome
now I can see the debian menu (don't know what I did).

XP is windoze ... It never works. 
Linux does well & much better, ... with time, you'll see ...

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> this sh*t is great
but I don't like KDE
it's really like winxp...
by the way - somehow my problem has been solved with gnome
now I can see the debian menu (don't know what I did).
I dont recall well :should be:
```
apt-get -f -y install menus 
```
or 
```
apt-get -f -y install menu
``` 
 
To have your debian-menu

or if it's not working, that will I guess:
```
apt-get -f -y install menu
apt-get -f -y install menus
apt-get -f -y install twm
```
(twn installs the debian menus if I receall well);)
  
Let me knwo which one works. ;) ;)

---

### Post by MaximB on 2006-08-04
yes I've typed thouse commands and installed thouse packages
but it didn't work right away
but after an hour it did for some reason...

and it's install [B]menu
[/B]and[B] debian menu
[/B]

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> yes I've typed thouse commands and installed thouse packages
but it didn't work right away
but after an hour it did for some reason...
 
you're damn fast to reply ! 
:D ;)

---

