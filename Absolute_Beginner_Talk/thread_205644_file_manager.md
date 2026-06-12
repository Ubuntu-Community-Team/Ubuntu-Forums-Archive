---
title: "file manager"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-28
hi all

can anyone recomment a file manager for KDE other than Konqueror i really dont like it much and would like to remove it altogether. if anyone has any suggestion would appreciate it

regards
niteblind

---

### Post by richbarna on 2006-06-28
[QUOTE=niteblind]hi all

can anyone recomment a file manager for KDE other than Konqueror i really dont like it much and would like to remove it altogether. if anyone has any suggestion would appreciate it

regards
niteblind[/QUOTE]

krusader is in the repos.

---

### Post by T700 on 2006-06-28
I suggest giving [krusader]("http://krusader.sourceforge.net/") a look.  It's got a ton of features and a nice, double pane display.  I would *not* remove Konqueror.  I suspect that you might hit some dependency problems.

Paul

---

### Post by az on 2006-06-28
[QUOTE=niteblind]hi all

can anyone recomment a file manager for KDE other than Konqueror i really dont like it much and would like to remove it altogether. if anyone has any suggestion would appreciate it

regards
niteblind[/QUOTE]
Gnome?

---

### Post by Jucato on 2006-06-28
Don't remove Konqueror just to be on the safe side.
Aside from Krusader, you could (almost) use any file manager available in Linux, but I'm just not sure how well they will perform their jobs outside of their respective desktop environments (Nautilus - GNOME, Thunar -Xfce, etc.)

What is it that you don't like about Konqueror? It just might be a setting that could be configured to do what you want. I must admit that Konqueror has a ton of features at first glance, but once you get used to how to set things up, you cn configure it anyway you like. If you could tell us what your issues with Konqueror are, we may be able to whip up a possible solution.

---

### Post by niteblind on 2006-06-29
what i dont like about konqueror is the way it displays the list view which i prefer to huge icons. my problem with it is VERY specific. i am partially sighted so i have change the colour scheme (which is also why gnome is out) but in the list view it overrides my colours and uses its own which makes it impossible for me to read every other line.

i know this is "my" but that sort of thing really gets up my wick being that is the main reason i moved from windows and gnome is not easily configurable and i cannot find a straight forward how to on the subhject

niteblind

---

### Post by niteblind on 2006-06-29
okay this is start to bug me!
i just install krusader and it does the same thing!
does anyone know where the icon view config file is for kde? it myst be the same file being used for all apps and i REALLY need to change the style

niteblind

---

### Post by Jucato on 2006-06-29
The problem here isn't really Konqueror's fault. It's in the color theme you are using. just a little modification is needed and you'll be a happy camper (I hope). 

The easy way is to actually change your color scheme. Open up System Settings, go to Appearance and choose Colors. Under the color schemes list, look for Keramik, click on it, then click Apply. 

But if you prefer to use a different color scheme, but don't what that annoying alternating colors in lists, here's how you can do it.
1. Open up System Settings, click on Appearance and then choose the Colors group.
2. Take note of what color is being used in "Standard Background". You can see which part of the window you are currently viewing at the drop down list for "Widget Color". You can see the color chooser immediately below it.
3. In that Widget Color drop down list, look for "Alternate Background in Lists". Chances are, its color is completely different from the color of "Standard Background".
4. Click on the color chooser directly below it and set it to exactly the same color as "Standard Background".
5. Click on Apply when you're done.

Btw, you do know that you can have a list view **with** large icons at the same time, right?

Hope that helps.

---

