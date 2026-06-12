---
title: "Gnome/KDE libraries question"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-10-18
I'm trying to come to grips with library loading.  Here are my questions:

1) At the moment, my system is Kubuntu, so presumably Ive loaded all (?) the KDE libraries on startup? If I had Ubuntu instead, would it have loaded all the Gnome libraries on startup?

2) Given that the answer to 1 is probably at least partially correct, and performance is a key issue, is it best on my Kubuntu system to stick to KDE apps (which use KDE libraries) since Gnome apps would load Gnome libraries?

3) Given that the answer to 2 is probably yes, do these newly loaded Gnome libraries 'unload' when the application which caused them to be loaded is closed thus leaving me with just my normal KDE libraries loaded in memory?

4) How do you know which libraries an application will use?  E.g. how do you know if an app is KDE/Gnome/XFCE?

5) I know that there are apps which aren't KDE or Gnome (or XFCE...).  Presumably this just means that they don't require those specific libraries?  Would such an app likely perform better than a Gnome app on my system since its libraries would likely be 'lighter' than loading all the Gnome ones?

Phew.  Hopefully this gives you an idea of the (rather poor) state of my knowledge.  Any help filling in the gaps gratefully appreciated!

---

### Post by GepettoBR on 2007-10-18
1)Completely correct.
2)Yes, although the difference isn't that big.
3)Don't really know
4)Many KDE(GNOME) applications have an outstanding letter K(G) somewhere in their name (like AmaroK, gparted, GIMP, Kino, etc.) Other than that, read the online documentation and the summaries in Synaptic.
5)Yes again.

By the way, I know this not from experience, but from asking in these forums just like you. Let's spread the knowledge :)

---

