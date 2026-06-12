---
title: "Installed KDE but still have a Gnome desktop"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Disorder on 2006-01-06
I've just installed KDE using sudo apt-get install KDM 

After I restarted(not because it prompted me to but because I forgot how to get back into the gui) I was brought to a Kubuntu login screen where I then logged in. However after logging in I was brought to the standard GDM.  How can I change this?

---

### Post by dragonfyre13 on 2006-01-06
Just find the "session" button on the login screen, and choose to start with KDE, instead of Gnome.

---

### Post by carlosqueso on 2006-01-06
You actually have only installed the desktop manager. you need ```
sudo apt-get install kde[CODE] or to install the total Kubuntu setup (you can use both) type [CODE]sudo apt-get install kubuntu-desktop
```  After you do this or if the M wass a typo, go to the sessions menu (it should be there) and choose KDE (or it may be Kubuntu, I don't use KDE) to get into it.

---

### Post by martinjanson on 2006-01-06
so if I do 
apt-get install KDE 
then I will have the KDE info for the software that needs that info?

---

### Post by Kimm on 2006-01-06
if you want kde, you have to do:

apt-get install kubuntu-desktop

or

apt-get install kde

Its realy not all that hard :)

---

### Post by poofyhairguy on 2006-01-06
You can use GDM with KDE. Just pick KDE in the "sessions" part.

---

### Post by Disorder on 2006-01-06
Thanks that worked perfectly

---

### Post by aysiu on 2006-01-07
[QUOTE=poofyhairguy]You can use GDM with KDE. Just pick KDE in the "sessions" part.[/QUOTE] Except that you won't be able to shut down from KDE, then.

---

### Post by patrick295767 on 2006-01-07
```
apt-get -f install kdm
```         is to install the login / password, made by kde 
  
```
apt-get -f install gdm
```         is to install the login / password, made by gdm (I prefer this one cos u can setup up more things)
  
```
apt-get -f install kde
```         is to install the gnome desktop
  
```
apt-get -f install gnome
```         is to install the kde desktop

Concerning ur session of fvwm, xfce, ... gnome, kde, you may select in the gdm or kdm (btw xdm exist too) , the X desktop u wanna use, eg fvwm.
U can use fvwm with apps of kde or gnome or xfce ... 
You are totally free of having for instance a 
fvwm with a kicker bar or gnome-panel bar with kde or gnome apps, with a scrolling of your pagers into ur desktop, like strategy games (age of empire ...)
  
Linux is cool,isnt it !

Greetings, 

Pat'

---

