---
title: "KDE &amp; Gnome"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Reaver on 2006-04-11
Hi people.

I've just recently installed Ubuntu 5.10, been playing about with it for a week or so now, as part of a dual boot with xp system, i've also got a copy of Kubuntu, and am keen to try out KDE.

What i'm curious about is there any way of dual installing both KDE and Gnome (so, adding KDE to my existing Ubuntu unstall) and being able to select between the two on boot up?

I had a quick look around but didn't find anything. No doubt i'm mising something blatantly obvious.

Thanks!

---

### Post by Darkriser on 2006-04-11
of course! install regular ubuntu and follow this link: [https://wiki.ubuntu.com/InstallingKDE](https://wiki.ubuntu.com/InstallingKDE)

---

### Post by AndyCooll on 2006-04-11
Try:

```
sudo apt-get install kubuntu-desktop
```

What that will give you is the Kubuntu desktop (i.e. KDE). Unless you change it, it will still default to the Gnome desktop but (before you login) it will now give you the option of selecting a "KDE" session if you wish.

:cool:

---

### Post by Reaver on 2006-04-11
Ah, that is awesome. Thank you both very much!

I'm almost slightly disappointed it's that simple!

Now to play around and see which one i can break first.

Cheers!

:D

---

### Post by Sef on 2006-04-11
> sudo apt-get install kubuntu-desktop

Before you do that (above), you should do this first:

sudo apt-get update

then install kubuntu

---

### Post by aysiu on 2006-04-11
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` This will make KDE easier to remove later if you decide to remove it. apt-get will not do that for you.

---

### Post by Reaver on 2006-04-11
Thanks very much, it'll be a while before i come to any sort of decision about which to keep and which to bin (why play with one new front end when you can have two i guess!) but i'll definitely give that a go.

---

### Post by m.musashi on 2006-04-11
Keep both. I switch around as my moods change. Sometimes I like KDE sometimes I like gnome. Of course I'm still learning so maybe someday I'll default to just one but this flexibility is one of the cool aspects of ubuntu imho.

---

### Post by Reaver on 2006-04-11
Cheers, it is great, one of my reasons for experimenting with ubuntu and moving away from Windoze was how restrictive it is, but i'm only just starting to realise the full scope of what linux can do.

---

### Post by Darkriser on 2006-04-12
[QUOTE=Reaver]Thanks very much, it'll be a while before i come to any sort of decision about which to keep and which to bin (why play with one new front end when you can have two i guess!) but i'll definitely give that a go.[/QUOTE]

Reaver, just to make you a little bit more confused (:mrgreen: ), there are not only TWO "front ends" (btw. correctly called window managers). If you try google, you'll find dozens of them. just for curiosity: [http://www.linux.org/apps/all/GUI/Window_Managers.html](http://www.linux.org/apps/all/GUI/Window_Managers.html)

---

### Post by Reaver on 2006-04-12
Ha, excellent, nothing like a little more confusion to sort through. Glad for it though, even more choice!

And thanks for the tip, i was wondering what the correct term for them was.  :D

---

### Post by m.musashi on 2006-04-12
In addition to gnome and KDE I've also played with XFCE. It's nice and light. I have it running on an old revived labtop c. win98. It loads quick and works which 98 no longer did. After 5 minutes trying to load gnome I gave up and went with XFCE. If you have old HW it's a nice option. I've heard a lot of people say nothing beats icewm. If you have a new(er) computer then gnome and KDE are good options - very customizable.

Anyway, have fun. If you are not aware [www.kde-look.org](www.kde-look.org) and [www.gnome-look.org](www.gnome-look.org) are good sites to find wallpapers, icons, themes and more to spruce up your wm.

---

### Post by Reaver on 2006-04-12
Thanks, i'll definitely give XFCE and icewm a look, running off an old compaq deskpro as a test machine at the moment, so anything that cuts down on resource usage is a bonus, once i've got my main box up and running i'm sure i'll spend a fair few hours looking at those sites to find the right 'look' for it! :D

---

