---
title: "Can't Uninstall Konquerer"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Grungydan on 2007-05-01
I am running Ubuntu Feisty, and I had used 

sudo aptitude install kubuntu-desktop

to put KDE on here so I could mess with it.  I decided to get rid of it and stick with Gnome for now, so I used

sudo aptitude remove kubuntu-desktop

to get rid of it.  It went through removing all of the KDE stuff, or so I thought.

I found that Konquerer and Konsole were both appearing in my Applications menu.  I tried to run

sudo aptitude remove konquerer

but it doesn't find it to remove it.  (0 packages, 0 bytes will be freed, etc)

I ran 

sudo aptitude remove konsole

and it found and removed it.

I still have Konquerer, and I can still launch it.  I've done a few searches but I was only able to find advice such as "use sudo aptitude remove" etc.  (The psychocats "Pure Gnome" page also just tells me to do what I have already tried.)

It's not the biggest deal in the world, but I'm just looking at it as an opportunity to learn something, so I'd like to get some suggestions on what to try next.   

If I have it and it runs, doesn't that mean that some of the KDE libraries are still in my install?  And if so, why does running sudo aptitude remove konquerer / kubuntu-desktop not do anything?  

An interesting conundrum. :)

---

### Post by Grungydan on 2007-05-01
Woooohooooo!  I managed to fix it (as near as I can tell).

I opened the Synaptic Package Manager, checked to view installed, and marked Konquerer and anything saying "KDE" for complete removal and applied the changes.

And no more Konquerer! :)

I just wonder if I'm going to find out that I broke something later.

---

