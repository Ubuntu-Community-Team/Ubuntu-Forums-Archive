---
title: "First Day Using Linux. Need Help."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by cinaibur on 2007-09-24
Hi all. I am a longtime windows user who finally decided to try out Linux. I am not very computer savvy by any means. I have a good desktop(2.8Ghz processor, 2GB ram, Nvidia GeForce 7900GTX video card). My question is, I know that the graphics on my computer are normally very crisp and sharp, after installing Ubuntu, they are fuzzy and not up to par. What Do I need to do to get my graphics working right? I apologize if this question is really dumb, but as I said, I am not very computer savvy. Any help is greatly appreciated!

---

### Post by alienexplorers on 2007-09-24
Go to > [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
and get the script called ENVY.  Use it to remove any drivers for your nvidia card, and then, use it to install the newest drivers.

---

### Post by cinaibur on 2007-09-24
Is that all I have to do? Should I turn of the Nvidia Accelerated Graphics Driver in the Restricted Drivers Manager?

---

### Post by alienexplorers on 2007-09-24
ENVY loads the most up to date drivers for your graphic card model.  There is no need to choose anything.

---

### Post by cinaibur on 2007-09-24
Thanks for the help! It worked wonders. I appreciate the straightforward answer. I know it was a stupid question.

---

### Post by alecwh on 2007-09-24
it wasn't a stupid question.

It might also be a resolution problem. If the fonts look stretched (if anything looks stretched) across the screen, post back here, I'll help you.

---

### Post by cinaibur on 2007-09-24
It was a resolution problem. I couldn't run my normal resolution until i ran ENVY. Everything seems to be ok now. Quick side question, can I upgrade to GNOME 2.20? I want to change up how my desktop looks. Default Ubuntu settings are very bland?

---

### Post by alecwh on 2007-09-24
for your first day using linux, I'm suprised you know what GNOME is! Short answer: no. You'll need to wait for gusty gibbon, which is due in October.

---

### Post by jordanmthomas on 2007-09-24
Luckily, there's no reason you can't change the appearance in gnome without having 2.2.20.
Have a look at gnome-look.org and you'll find a boatload of themes you can install.

---

### Post by cinaibur on 2007-09-24
lol. I have friends that always talk about using it. So if I can't upgrade, how do I make the desktop look better?

---

### Post by cinaibur on 2007-09-24
> **jordanmthomas said:**
> Luckily, there's no reason you can't change the appearance in gnome without having 2.2.20.
Have a look at gnome-look.org and you'll find a boatload of themes you can install.

k. thanks. I'll try it out

---

### Post by alecwh on 2007-09-24
I'd check out Compiz-Fusion too. many people don't recommend it, especially to beginners, but it's actually pretty stable now IMO. Just do a search, you'll get a million results.

Beryl is also something you might want to look into.

---

### Post by slira on 2007-09-24
> **cinaibur said:**
> lol. I have friends that always talk about using it. So if I can't upgrade, how do I make the desktop look better?

try KDE; it looks great...

in a shell do

[FONT="Courier New"]sudo apt-get install kubuntu-desktop[/FONT]

next time you reboot chose kde as default

best
slira

---

### Post by dptxp on 2007-09-24
Looks are not likely to get better with newer version of Gnome.
You have to learn how to make changes.

To try KDE use kde-core, the smaller one, not kubuntu-desktop.
Personally I do not like KDE, but many do. KDE is less stable and
Gnome is simple to navigate.

---

