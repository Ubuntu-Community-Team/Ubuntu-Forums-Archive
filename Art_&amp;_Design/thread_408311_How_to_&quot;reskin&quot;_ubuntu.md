---
title: "How to &quot;reskin&quot; ubuntu?"
date: 2007-04-13
forum: Art &amp; Design
---

### Post by Gorthus on 2007-04-13
Hello everyone...

I'm new to Ubuntu, and some of the screenshots that people have posted are pretty neat, but I don't think they are possible with barebones ubuntu.

Can anyone tell me what i need to change the UI around, and how to install it?

Thanks,
Gorthus

---

### Post by dunedust on 2007-04-13
I followed this guide to customize my desktop

*[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)*

hope it helps

---

### Post by ComplexNumber on 2007-04-13
> **Gorthus said:**
> Hello everyone...

I'm new to Ubuntu, and some of the screenshots that people have posted are pretty neat, but I don't think they are possible with barebones ubuntu.

Can anyone tell me what i need to change the UI around, and how to install it?

Thanks,
Gorthus
the first ting i would do is to install gtk2-engines-pixbuf. thats a theming engine and is responsible for drawing the actual widgets such as scrollbars, toolbars, menus etc. lots of themes make use of that engine, so you will invariably have to use to at some point. another good engine is the murrina engine (the deb for it is availble in the murrina thread h[ere]("http://ubuntuforums.org/showthread.php?t=239378&page=43")).

then you can go over to gnome-look [here]("http://gnome-look.org/") and download some themes. now, i've already mentioned what theme engines are. there are other components to skinning ubuntu - for example, icon themes, gtk themes, and metacity themes. there are are beryl themes too, but we'll leave that for the time being. the gtk themes modify the colour of the various widgets and also their dimensions etc. metacity themes modify the wndow borders.

to install a theme, you need to be aware of where they go. gtk themes and metacity themes go in /usr/share/themes, and .themes in your home directory. if you install it in the former, then the theme can be used by everyone including root. you will find that, if you install them in .themes in your home directory, applications that are run by root (ie when you type in your password to run them) will look strange. best to install gtk and metacity themes in /usr/share/themes.

icon themes go in /usr/share/icons, and in .icons in your home directory.


after you've downloaded a theme to your home directory, right click on it and select 'extract here'. it should extract to become the name of the directory, but just have a look inside to see if there is more than 1 theme. for example, it may extract to a directory called lily_FILES, but when you look inside, it has lily_blue and lily_pink. if you look further into each one, you will find a "metacity-1" and/or a "gtk-2.0" directory. you need to take the actual folders that have the name of the actual theme - in that example, lily_blue and lily_pink.

then fire up the commandline and go to where the themes are. then type in the following:
s[B]udo cp -R <name-of-theme> /usr/share/themes (for gtk and metacity themes)
sudo cp -R <name-of-theme> /usr/share/icons (for icon themes)[/B]

---

### Post by Gorthus on 2007-04-13
Thanks very much guys... I think I can figure the rest out...

I only have one question:

How do I get a panel to not make windows move up, yet still stay there... So like autohide mode but it doesnt hide?

---

### Post by tom56 on 2007-04-13
> **Gorthus said:**
> How do I get a panel to not make windows move up, yet still stay there... So like autohide mode but it doesnt hide?

I understand what you mean but I don't think it can be done. You can manually hide which would in practice be more or less the same. Instead of having to minimize windows to get to the panel you'd just need one click on the arrow.

The option is in the same menu as autohide.

---

### Post by Gorthus on 2007-04-13
Meh... I'd rather just have it be "always on top"

---

