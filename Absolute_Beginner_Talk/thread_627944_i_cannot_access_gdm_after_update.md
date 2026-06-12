---
title: "i cannot access gdm after update"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2007-11-30
i have a problem with my ubuntu gutsy after update,and upgrade of 1 thing i restart my pc but i the desktop its different its its a blue desktop with alot feautures missing and an icon on the top like star which says ''new item,this item has not yet been configured''..its not failsafe.
.i try to run gnome-enviroment from the terminal but it says that i am on a gnome enviroment..this is the second time this happens the first time i reinstall ubuntu to solve the problem.hope there is a different way to solve that.. the problem is i cant see if there is other manager to remove it.
this is snapshot of my desktop
[IMG]http://img.photobucket.com/albums/v665/psychofemale69/snapshot1.png[/IMG]

---

### Post by SunnyRabbiera on 2007-11-30
you can try apt-get install xubuntu or kubuntu desktop...
this might help give you some kind of GUI

ah, looks like XFCE there..
are you using xubuntu instead of ubuntu?

---

### Post by psychobeauty on 2007-11-30
i install for the second time ubuntu 7.10 yesterday it was working fine after some automatic updates that i accept...

---

### Post by psychobeauty on 2007-11-30
YEAH you have right is xfce enviroment..
i went to the ''settings manager'' and is says ''xfce desktop''

how did that come??how can i change it to gnome?

---

### Post by Sef on 2007-11-30
> how did that come??how can i change it to gnome?

At the log in window, where you put in your name and password, there is a button in the bottom left corner called options.   Options > Sessions > Gnome

---

### Post by psychobeauty on 2007-11-30
thanx thats solve the problem..but can u tell me why its turn in xfce after upgrade??

---

### Post by Dr Small on 2007-11-30
> **psychobeauty said:**
> thanx thats solve the problem..but can u tell me why its turn in xfce after upgrade??
Apparently it downloaded it (for some unknown reason), when you upgraded.

---

### Post by psychobeauty on 2007-11-30
> **Dr Small said:**
> Apparently it downloaded it (for some unknown reason), when you upgraded.

ok thanx do i must delete it???to have only one manager??

---

### Post by Dr Small on 2007-11-30
You can keep it and use it if you want, but if not, just remove it:
```
sudo apt-get remove xubuntu-desktop
```

---

