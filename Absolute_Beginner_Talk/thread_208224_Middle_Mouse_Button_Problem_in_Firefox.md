---
title: "Middle Mouse Button Problem in Firefox"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by krazykirk on 2006-07-03
Hi there everyone!

I'm relatively new to Ubuntu, but i'm picking it up pretty quickly, (the command line doesn't scare me anymore lol) and it's fantastic!

Theres just a pretty big annoyance in firefox. In windows, when you press the middle mouse button anywhere in the page you get that autoscroll thing going on, and when you middle click a tab, it closes. But in ubuntu, for some bizarre reason i think it restores a previously closed tab! I think this could be fixed in the about:config area in firefox but I'm not exactly sure where. 

If this might be hardware related, I have a logitech cordless optical mouse.

Thanks in advance!

---

### Post by bollix47 on 2006-07-03
It could be hardware related in which case there are a number of threads about logitech mice in the firefox forums.

Take a look at

tools - options - advanced

Is the "Use auto-scrolling" box checked?

---

### Post by adam.tropics on 2006-07-03
[QUOTE=krazykirk]Hi there everyone!

I'm relatively new to Ubuntu, but i'm picking it up pretty quickly, (the command line doesn't scare me anymore lol) and it's fantastic!

Theres just a pretty big annoyance in firefox. In windows, when you press the middle mouse button anywhere in the page you get that autoscroll thing going on, and when you middle click a tab, it closes. But in ubuntu, for some bizarre reason i think it restores a previously closed tab! I think this could be fixed in the about:config area in firefox but I'm not exactly sure where. 

If this might be hardware related, I have a logitech cordless optical mouse.

Thanks in advance![/QUOTE]


The auto scroll, in about:config, set 'general.autoScroll' to true.
As for the tabs, as far as I know there are a few good extensions which would give you that functionality, but I can't find it in about:config as is by default.

---

### Post by Jucato on 2006-07-03
just confirming that bollix47's answer is the way to do it. :D

---

### Post by adam.tropics on 2006-07-03
> just confirming that bollix47's answer is the way to do it.

Possibly the simplest, granted, but either will do it!

---

### Post by Jucato on 2006-07-03
[quote=adam.tropics]Possibly the simplest, granted, but either will do it![/quote]

Sorry, didn't mean to discredit your method in anyway. :mad:

---

### Post by krazykirk on 2006-07-04
It works! Thanks for the help everyone! :)

I wonder why that option is switched off by default.... o_O

---

### Post by nanotube on 2006-07-04
also, for middleclick to close the tab, set middlemouse.contentLoadURL to false (using about:config)

---

### Post by Jucato on 2006-07-04
@nanotube: The Firefox version in Ubuntu (1.5.0.3+) already has middle-click set to close tabs. I'm not sure if that's an Ubuntu-only setting, or something common to all Firefox.

---

### Post by nanotube on 2006-07-04
[QUOTE=Fenyx]@nanotube: The Firefox version in Ubuntu (1.5.0.3+) already has middle-click set to close tabs. I'm not sure if that's an Ubuntu-only setting, or something common to all Firefox.[/QUOTE]
i'm not sure either... but he asked about it, so i mentioned it. :)

---

### Post by adam.tropics on 2006-07-04
[QUOTE=Fenyx]@nanotube: The Firefox version in Ubuntu (1.5.0.3+) already has middle-click set to close tabs. I'm not sure if that's an Ubuntu-only setting, or something common to all Firefox.[/QUOTE]
Feel silly now, I only knew about the middle click to open link in a new tab, I never knew clicking on the tab closed it!! I have been using the context menu all this time!

---

### Post by nanotube on 2006-07-04
[QUOTE=adam.tropics]Feel silly now, I only knew about the middle click to open link in a new tab, I never knew clicking on the tab closed it!! I have been using the context menu all this time![/QUOTE]
hehe, well, now you know. :)

---

