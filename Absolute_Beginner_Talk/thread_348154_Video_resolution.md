---
title: "Video resolution"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Kenny101 on 2007-01-28
Ok well first i've known about linux for several years but am still a relative new user to it. I perfer it over windows but sadly don't know that much about it. 

My problem is, and i guess I should clarify that i'm using Ubuntu 6.06, my problem is that when I start up linux the resolution is 640x480. I also use a 19' LCD monitor but i don't know if thats part of the problem. The major problem I know some of you might say is, just use the drop down menu and change your resolution to one you perfer. Well the dropdown menu is not there. Sure I can click it but no menu appears nor does it allow in ANY change in the size of the screen. 

Its fustrating because with out getting the resolution right, I can't see all of my windows, the problem with that is I can't do an install of my linux if i can't click on the install button cos i can't see the entire application. :( any help or advice would be appreciated.

---

### Post by taurus on 2007-01-28
Sounds like you have to install a driver for your graphic card and what is it anyway?

---

### Post by ljpm on 2007-01-28
Before posting search the forum for the answer. 

run the following from terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

Make sure you enter he correct Hscan and Vscan values for your monitor.

---

### Post by Kenny101 on 2007-01-29
I just downloaded 6.10 or Kubuntu 6.10 and all is well. Thanks for the help guys. 

Btw my video card is a Ati Radeon X800.

---

