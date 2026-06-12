---
title: "Background in Ubuntu"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by hoarythehedgehog2009 on 2006-04-09
As you can see from my question, I am very new to Ubuntu and Linux:
How do you change your background in Ubuntu?:) 

___________
Dual Booting Windows XP and Breezy

---

### Post by Perfect Storm on 2006-04-09
System tab ---> Preferences ---> Desktop Background

---

### Post by catlett on 2006-04-09
Or, when your pointer is sitting on the desk top, right click. An option box drops down and you can choose "change background". When you make this choice a window opens with the desktop configurer. Just scroll through the choices to the one you like or choose "add wallpaper". This will let you choose a picture you have saved. Plus go to the GnomeArt.org website,  it has a big selection.

---

### Post by clareb on 2006-04-09
You can drag a picture into the 'Desktop Background Preferences' window as well and it will automaticaly replace the one you're using. I keep all my wallpapers in a separate folder as well, though, because sometimes they do just disappear from the Backgrounds window. Hope that made sense ;~)

---

### Post by patrick295767 on 2006-04-09
```
sudo apt-get -f -y install xloadimage
xloadimage -onroot -fullscreen ~/.wallpaper
```

works also i guess under gnome

#######"
even better : funny one :
> apt-get -f -y install xscreensaver
cd /usr/lib/xscreensaver
./pong -root


---

