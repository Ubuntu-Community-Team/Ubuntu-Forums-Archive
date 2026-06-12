---
title: "Color Depth?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-29
How do I change my color depth under Ubuntu?

---

### Post by baldy1324 on 2006-09-29
run ```
sudo gedit /etc/xorg.conf
```
scroll down to the part where it says your resolutions. there should be multiple entries for each color depth (24 being the highest).
p.s. if you want 32-bit depth it is the same thing as 24 exept is has a different way of displaying color. so you cant have 32-bit but there isn't a reason to want it.

---

### Post by madmetal on 2006-09-29
one little mistake..
sudo gedit /etc/X11/xorg.conf

;)

---

### Post by koopaloop on 2006-11-06
hi, i have the same problem. i get as far as tpying "sudo gedit /etc/X11/xorg.conf" into the terminal, but when i try to type in the password, it doesn't take. i try to type my password in, but the keys don't show up

plz help :S

---

### Post by ewl1217 on 2006-11-06
When you use sudo, there is no indication that your password is being entered. Just enter it as normal.

---

### Post by koopaloop on 2006-11-06
yes :) getting there, so i entered "gedit /etc/X11/xorg.conf", and i scrolled down to the graphics controller to change the color depth from 16 to 24. after i delete 16 and type in 24, what do i do? press enter?

---

### Post by lemonsCC on 2006-11-06
save then exit

restart

---

### Post by koopaloop on 2006-11-06
it won't let me,
it says

Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

does it have anything to do with it being "read-only"?

---

### Post by jeffathehutt on 2006-11-06
You need to type "gksudo gedit /etc/X11/xorg.conf", that way you can save the changes.

---

### Post by koopaloop on 2006-11-06
thanks soo much guys :) works perfectly

---

### Post by Wangsta on 2006-11-08
What the crap?? I'm using edgy eft and i can't change my color depth, and "gedit" isn't even a command! what am i doing wrong!?

---

### Post by Velotix on 2006-11-08
The big giveaway is in the name: **gedit**. There are several versions of Ubuntu that use different types of desktops. Xubuntu, what I'm using, uses Xfce, for example, Kubuntu uses KDE, and Ubuntu uses **G**NOME. Note that G: generally, to make it easier to tell which command belongs to which desktop, they have names beginning with g, k or x to match the environment they use.

In other words, **gedit** only works for GNOME unless you make a point of installing compatibility drivers, so I guess you're not using regular Ubuntu. You probably need the equivalent command for KDE or Xfce depending on what you're using.

You can always edit the xorg.conf file manually, though I'm not sure how you recover your original settings if you make a mess of things.

---

### Post by CatKiller on 2006-11-08
```
sudo nano /etc/X11/xorg.conf
``` will work whatever. ```
kdesu kate /etc/X11/xorg.conf
``` will work in Kubuntu. I don't know what it would be for Xubuntu.

In all cases, ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` should be used before making any changes.

---

