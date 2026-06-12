---
title: "Just installed"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Larh on 2006-01-15
Hello folks.

I've just got Ubuntu running on a Celeron(p3 equivelent) 400mhz CPU with 64meg of ram(8 of which is used for the onboard video, I had to tweak it down to 2 for the installer to work) a 10.2gig hard drive. 

My question is, is it possible to streamline the OS alittle bit further, so it will run just a bit faster for me. At the moment this is the only box I have available to run a linux setup on, and so far I really like the results. If this has been answered I couldn't find anything specific to my needs with search... a point in the right direction would be great.

Any help is much appreciated! (please explain in some detail, still working out how things work 1st day of linux!)

---

### Post by simon_is_learning on 2006-01-15
64mb Ram, I've been there too...

Have you read the Ubuntu Mini Ram howto?
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Thats one alternative...

The other one (very simular but much easier) Is installing Xubuntu

after you have done a server installation, uncomment sources.list, update, and do a apt-get install xubuntu-desktop

startx....kabahamm...
also maybe a login manager can be an atractive application ;)
do a apt-get install gdm
gdm finds XFCE automaticly

---

### Post by hen3rz on 2006-01-15
Hello,

Just the other day i installed a very minimal ubuntu install on an old laptop with 64mb of ram and a 4gig hdd and it now runs like a beast, this is what i did.

Typed "Server" as my choice of install

Once installed I logged in as root and typed in the following:

```
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal synaptic
```

I then restarted and was left with a simple gui with no programs installed.

---

### Post by simon_is_learning on 2006-01-17
hen3rz: 
Have you compared Metacity to fluxbox?
I have for now Fluxbox as WM, and i can recomend it for low RAM, but the startup time for fluxbox is longer then for XFCE...

could you give me your opinion on Metacity as a window Manager?

---

### Post by hen3rz on 2006-01-17
> hen3rz:
Have you compared Metacity to fluxbox?
I have for now Fluxbox as WM, and i can recomend it for low RAM, but the startup time for fluxbox is longer then for XFCE...

could you give me your opinion on Metacity as a window Manager?

Unfortunatley i havent ever dealt with fluxbox but only Metacity so i cannot give an oppinion on how they compare against each other but i can say that i have only heard good things about fluxbox as a WM for low ram pc's just as you mentioned.

Also just as a side note Metaciy runs fairly lagishley on my old laptop but nothing that would hinder everyday use.

---

