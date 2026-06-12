---
title: "Ubuntu-Kubunto Logo During Startup"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by marianoi on 2007-03-07
Hello,

I'd have a question for you guys...

I have both Ubuntu and Kubuntu installed on my PC. I first installed Kubuntu from the CD and then installed "ubuntu-desktop" on top.

I would like to change the Kubuntu logo (usplash?) that shows up after the boot loader to the Ubuntu one, which IMHO looks much nicer....does anyone know how to do it? :) 

Thanks!

Mariano

---

### Post by o_fortuna on 2007-03-07
It shouldn't be too hard. The easiest way I can think of is to open a terminal window (Applications--Accessories--Terminal) and type
```
sudo update-alternatives --config usplash-artwork.so
```
Then just select the number for /usr/lib/usplash/usplash-theme-ubuntu.so

Information from [http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/]("http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/")

---

### Post by marianoi on 2007-03-07
Fantastic!

Thanks a lot!

:)

---

