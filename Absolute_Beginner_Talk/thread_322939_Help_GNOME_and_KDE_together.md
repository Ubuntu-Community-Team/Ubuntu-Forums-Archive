---
title: "Help: GNOME and KDE together"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by ngch on 2006-12-21
I've been using the GNOME interface with Ubuntu Drapper for quite some time now, and I want to try out KDE. I have read that it is possible to install GNOME and KDE together.

Can I accidentally break my system if I do so? Can I use GNOME programs in KDE? How do I remove KDE/GNOME if I decide I dun want either of them anymore? I am a noob to linux in general, so pls be patient with me :p

---

### Post by meng on 2006-12-21
It shouldn't break your system. You can run GNOME programs in KDE and vice versa. Look here for more detail on converting back to pure GNOME/KDE:
[www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

---

### Post by Eddy Dean on 2006-12-21
It's really easy to do so, and you're not likely to mess up. [www.ubuntuguide.org](www.ubuntuguide.org) explains how to do so. To start using kde you need to click "sessions" on the login screen and then select KDE instead of GNOME.


Greetz,
Arno

---

### Post by Sef on 2006-12-21
> Can I use GNOME programs in KDE?

Yes, you can, and you can use KDE programs in GNOME.

---

### Post by taurus on 2006-12-21
You can run KDE apps in Gnome or vice versa.  I always use k3b to do all my burning even though I use Gnome.  So, if you want to install KDE, do

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
And if you want to remove either one, read these guides then...

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by CroEragon on 2006-12-21
I read somwhere that for some reason you should use just code below (do not ask me i don't know, i just know that i used it to install my kde and it worked perfectly.)
```
sudo apt-get install kubuntu-desktop
```
Just be aware that if you use this code your boot splash image and login will be changed to Kubuntu version also.
When you get to login you can simply choose GNOME or KDE and make default one of them if you want.

---

### Post by psycosmyth on 2006-12-21
Only problem i had was the menus, KDE apps are automaticaly put in weird places in Gnome and vice-versa. I had a tri-factor er...quad....flux too and it was too cluttered for me.

---

### Post by TooRight on 2006-12-21
I used

> 
sudo apt-get install kubuntu-desktop


to install kubuntu on my system. I sooo loveeeeeeeeee it!! You are so much more in command of everything and the eyecandy is incredible!!

---

### Post by ngch on 2006-12-21
Thanks guys! Now I am ready to try out KDE! :)

---

### Post by keithpeter on 2006-12-22
> **TooRight said:**
> I used

```

sudo apt-get install kubuntu-desktop

```

to install kubuntu on my system. I sooo loveeeeeeeeee it!! You are so much more in command of everything and the eyecandy is incredible!!

Yes, all very jolly! Health warning: I had installed OpenOffice 2.1 manually using alien and the RPMs from the OpenOffice Web site. Installing the kubuntu-desktop appears to have over-written part of the Office installation in such a way that I can't use it from either of the desktops. I think that might be a case of me being too clever and to quick with the 'return' when using apt-get :-)

---

### Post by TooRight on 2006-12-22
Oh no!! Ohh mannn, that must be frustrating!! Have ya tried reinstalling it yet?

---

### Post by sailor2001 on 2006-12-22
I have found that just installing kde from synaptics is the easiest for me....and gives me no problems what so ever, in gnome or in kde

---

### Post by floke on 2006-12-22
I agree. Synaptic is much better. Loved KDE at first, but Gnome is where the heart is:mrgreen: 
Still, I love being able to choose. And Enlightenment's not bad either!

---

