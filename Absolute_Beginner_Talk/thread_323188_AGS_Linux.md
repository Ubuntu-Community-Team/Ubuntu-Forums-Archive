---
title: "AGS Linux"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2006-12-21
Hi,
I've just recently upgraded to Ubuntu from Windows, and I'm pretty new to all of this. However, I found a port of AGS (Adventure Game Studio) that allows me to run AGS made games on Linux. Unfortunately, I have no idea how to install this thing. You can find it on: [http://drevil.warpcore.org/ags/](http://drevil.warpcore.org/ags/)

It seems to be made for Red Hat, but I think it could be possible to make it work with Ubuntu. 
For that matter, though, how do I install this with Synaptic? It gave me an error of a missing archive. What do I need to do?

---

### Post by Ecthelion on 2006-12-22
> Hi,
I've just recently upgraded to Ubuntu from Windows, and I'm pretty new to all of this. However, I found a port of AGS (Adventure Game Studio) that allows me to run AGS made games on Linux. Unfortunately, I have no idea how to install this thing. You can find it on: [http://drevil.warpcore.org/ags/](http://drevil.warpcore.org/ags/)

It seems to be made for Red Hat, but I think it could be possible to make it work with Ubuntu.
For that matter, though, how do I install this with Synaptic? It gave me an error of a missing archive. What do I need to do?


Those rpm are for allegro and are indeed redhat packages.
You can convert rpm to .deb if you want.
You need to have alien and fakeroot for that:
```
sudo apt-get install fakeroot alien
```
Then do
```
fakeroot alien *<name of the rpm package>.rpm*
```
and you'll have a .deb package.
For installing .deb packages just do
```
sudo dpkg -i *<place and name of the .deb package>*
```

> It gave me an error of a missing archive. What do I need to do?
If the error you had was about a missing xml library, then just install it
```
sudo apt-get install libxml1
```

I hope this helps..

---

