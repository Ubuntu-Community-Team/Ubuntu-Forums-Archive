---
title: "No desktop manager"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-05-22
Hi,

I've been spending a bit of time lately seeing the sights and hearing the sounds of the other flavours of Ubuntu. 

Using this [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) as a guide for installing and removing the different desktop environments. Now i have managed to remove all the desktop environments  so i get the terminal after the OS has booted up. 

Currently running a 7.04 live CD (well USB)

is there anyway i can get A desktop environment back.

Thanks 

        Simran

---

### Post by taurus on 2007-05-22
```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
```

---

### Post by Simran on 2007-05-22
Ah. thank jesus taurus is here to save the day ! xD

So if i do this now, whilst running the Live image from my USB disk it will install them to my hard drive or the usb stick ?

Simran

---

### Post by taurus on 2007-05-22
You need to boot into Ubuntu on the harddrive first before you can install a window manager.  

Can you boot Ubuntu from your harddrive?

---

### Post by Simran on 2007-05-22
yeah, i did. I was unsure if the internet would work through the command line so i just ran apt-get install kubuntu-desktop and job done.

Thanks, as simple as it may seem to you :P these tasks are mammouth to me :)

Simran

---

