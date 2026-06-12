---
title: "Changing to KDE"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by lgmdaniel on 2005-12-19
So whats the easiest way for me to switch from Gnome to KDE as it doesn't seem easily aparent from the menu choices I have.

---

### Post by gerbman on 2005-12-19
[QUOTE=lgmdaniel]So whats the easiest way for me to switch from Gnome to KDE as it doesn't seem easily aparent from the menu choices I have.[/QUOTE]

All you should need to do is install KDE with synaptic and select KDE when logging back in.

---

### Post by patrick295767 on 2005-12-19
```

apt -y -f install gdm 
apt -y -f install kde 
```
    
then 
```
su
/etc/init.d/gdm start
```
  
then, bottom left corner (one of 3 icons), u may select if you 'd like to use : gnome, kde , fvwm ... (if installed)
  
Enjoy Kde !!

---

### Post by lgmdaniel on 2005-12-19
Cheers.. I'll be having a go when I get home tonight.

---

### Post by .t. on 2005-12-19
If you are in Ubuntu, the best way to do it (I think, having got Kubuntu, I am not that sure), is to go:```
sudo apt-get install kubuntu-desktop
```; that will install everything you need for KDE, and with all the Kubuntu tweaks.

---

### Post by lgmdaniel on 2006-01-03
[QUOTE=.t.]If you are in Ubuntu, the best way to do it (I think, having got Kubuntu, I am not that sure), is to go:```
sudo apt-get install kubuntu-desktop
```; that will install everything you need for KDE, and with all the Kubuntu tweaks.[/QUOTE]


I used this command and it worked just great, might get some time to look at it now christmas is over and I'm not fixing anymore PC's.

---

