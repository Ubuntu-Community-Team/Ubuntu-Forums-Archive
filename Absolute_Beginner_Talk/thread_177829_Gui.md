---
title: "Gui"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Israfel on 2006-05-16
I have kubuntu installed and am having no problem booting into it or my winXP;however, when I boot kubuntu,there is no GUI. After logging in from this screen i get (username@ubuntu):$~. How do i acess the GUI?

---

### Post by Dr. Nick on 2006-05-16
type 
startx

It may give you errors, if so post here if you need help

---

### Post by Israfel on 2006-05-16
Will do. Thanks (I'll be back in all likelihood O_o).

---

### Post by Israfel on 2006-05-16
fatal IO error 104 (connection reset by peer) at X server ":0.0" or something similar. I also had to ctrl+alt+f1 to get to a screen where I could log in.

---

### Post by nanotube on 2006-05-17
well, something is wrong with the xserver config. run command
sudo dpkg-reconfigure xserver-xorg
and try changing some settings.

if you want a quick way to get a functioning xserver, you could also just edit your /etc/X11/xorg.conf file, and find the line that looks like
```
Device "ati"
```
(or Device "nv", depending on what your graphics card is)
and change it to 
```
Device "vesa"
```
save, and try startx again.
that will leave you without 3d accel, but at least you will have a gui, and you can play with that stuff afterwards.

out of curiosity, what video card do you have?

---

### Post by Israfel on 2006-05-17
All I seem to be able to find out about it is that it's an ATI.

---

### Post by Israfel on 2006-05-17
I used sudo dpkg-reconfigure xserver-xorg and went through the menu, it seemed to recognize everything; but even after this startx failed to work.

---

### Post by Israfel on 2006-05-17
If anyone has any suggestions, contact me at [email]tabkey@hush.net[/email]. (sice I can't stay on the  forums much longer tonight).

---

### Post by mostwanted on 2006-05-17
You can always dig up this topic again using quick links > my profile > view my posts link.

---

### Post by Israfel on 2006-05-17
When using the sudo dpkg-reconfigure xserver-xorg  command; do i need to use another command to enable/save the changes made?

---

### Post by Israfel on 2006-05-17
And my video card is an ATI Radeon XPRESS 200M series.

---

### Post by r4ik on 2006-05-17
From the command-line type youre usrname and passwwrd hit enter.
Do a,

sudo dpkg-reconfigure xserver-xorg and hit enter,

just follow the defaults until you get to youre grapics card section select "nv" for Nvidia or "vesa" (ATI)

continue and finish with,

sudo /etc/init.d/gdm stop =>enter

sudo /etc/init.d/gdm start =>enter

Good luck !
__________________

---

