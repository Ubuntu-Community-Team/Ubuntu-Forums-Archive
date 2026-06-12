---
title: "Games"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by Goffy on 2005-10-02
After figuring out the basics around the synaptic package manager and the extra repositories I found
a lot of interesting games I tried to download and install.

I found a flight simulator, a panzergeneral clone and doom or was it maybe quake. Everything seemingly went fine with the installation as no error messages occured, but after the process it seems they haven't been installed after all, or at least aren't accessible through the menu.

What could be wrong?

---

### Post by whiterabbit on 2005-10-02
Try loading via (k)console.  Proggies like earth3d won't show up in the applications menu but when ./earth3d (or similar) is typed, it usually works.  Can't help with much else, sorry.  I'm quite new myself.

---

### Post by Perfect Storm on 2005-10-02
It's properly the 3D card accelerator drive that isn't setup.

Edit: Sorry, I read your post wrongly.
Try
```
killall gnome-panel

```
and see if the appear in te game tabs

---

### Post by phen on 2005-10-02
open up a terminal, and try. if you installed quake for example, try typing quake.
if you can't find a game, try  panz<press tab once or twice> to find every command on your computer starting with panz. you would find quake by typing q<tab twice>

you open a terminal by either right click on desktop or from the menu.  
you can add menu entries for the games with a tool called smeg. you find it in synaptic

have fun!

---

### Post by Ampersand on 2005-10-02
For programs installed via synaptic, you generally won't require the ./ , since it just means 'in this directory'.

---

### Post by whiterabbit on 2005-10-02
Ah, fair enough.  

Still, loading via terminal should work if it installed correctly.

---

### Post by Goffy on 2005-10-02
OK.. The search through terminal worked fine. I found quake. However it is important to write down the names so that one knows what to look for..

Quake didn't work. A dependant file didn't install. Don't know where to look for it. smeg won't install at all as it doesn't find a dependant programme; a python thingy it seems..

Yes, yes I know... but I'm learning.. :lol:

---

### Post by Perfect Storm on 2005-10-02
There's some problem with smeg, you are not the only one ;)

---

