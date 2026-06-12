---
title: "Cammands given to icons/launchers"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-18
In the "cammand" option for creating icons/launchers what exactly am I suppose to put.  For example, if on the desktop if I put an icon that has the cammand "Opera" (and I have it installed) then when I click on it, it will open Opera.  But when I put it in a toolbar (this is in xfce) and use the same cammand it will claim that there is no such file or directory.  What gives?

---

### Post by Kilz on 2006-06-18
[QUOTE=WADemosthenes]In the "cammand" option for creating icons/launchers what exactly am I suppose to put.  For example, if on the desktop if I put an icon that has the cammand "Opera" (and I have it installed) then when I click on it, it will open Opera.  But when I put it in a toolbar (this is in xfce) and use the same cammand it will claim that there is no such file or directory.  What gives?[/QUOTE]
I have a server I put xfce on, Im not exactly happy with it, but I find that the path to the executable works best. Most of them will be in /usr/bin

---

### Post by aysiu on 2006-06-18
I've not experienced that.

---

### Post by 5-HT on 2006-06-18
[quote=Kilz]I have a server I put xfce on, Im not exactly happy with it, but I find that the path to the executable works best. Most of them will be in /usr/bin[/quote] 
Just to add to Kilz's post, to find the executable for the program you want in a launcher you can use 'which':

```
which <program>
``` 
e.g., for vim ```
$which vim
/usr/bin/vim 
``` 
Does it help if you place the absolute path to the executable (output from which) in the command field for the launcher?

---

### Post by Kilz on 2006-06-18
[QUOTE=aysiu]I've not experienced that.[/QUOTE]
Xfce has a lot of quirks, imho its not quite as polished and gnome or kde and needs some work. I put it on a server so it wasnt a big deal to me. I need a gui to run valknut as the server runs a dc++ hub and I leave the client on 24/7. But one that didnt use a lot of resources.  But I wouldnt recommend Xfce for someone to use day in and day out.

---

