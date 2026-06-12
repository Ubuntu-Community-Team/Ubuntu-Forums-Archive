---
title: "No Icons"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Benjamin Poulton on 2007-03-29
I have installed Ubuntu, but when I get into the OS no icons appear. All that is there is the Ubuntu wall paper. How do I get Ubuntu up and running?

---

### Post by oilchangeguy on 2007-03-29
if you've installed it, and gotten to the desktop, it is up and running. what are you trying to do? and by default there are no icons on the desktop.

---

### Post by Benjamin Poulton on 2007-03-29
There is nothing there. Like I can't do anything? nothing to click on, nowhere to add commands, nothing!

---

### Post by oilchangeguy on 2007-03-29
in the top panel do you not see, applications, places, system?

---

### Post by Benjamin Poulton on 2007-03-29
Nope... nothing. Just the wallpaper.

---

### Post by oilchangeguy on 2007-03-29
what version of ubuntu are you running?

---

### Post by Benjamin Poulton on 2007-03-29
6.10 i386

---

### Post by oilchangeguy on 2007-03-29
try, Alt F2, and enter gnome-panel. and see what happens.

---

### Post by ComplexNumber on 2007-03-29
> **Benjamin Poulton said:**
> I have installed Ubuntu, but when I get into the OS no icons appear. All that is there is the Ubuntu wall paper. How do I get Ubuntu up and running?
fire up the terminal and type in gconf-editor. in gconf-editor, go to the 'Edit' enu, then slect 'Find'. type in 'nautilus', but leave the tickboxes unticked. go to apps/nautilus/desktop. now make the icons visible.


btw the system tools entry in the menu isn't shown by default in ubuntu edgy. to make it visible. right click on the applications menu, select 'edit menu'. then make the 'system tools' entry visible. in there, you will find gconf-editor(aka configuration editor) and other tools.

---

### Post by Benjamin Poulton on 2007-03-29
Nothing happens when I hit ATL F2

---

### Post by oilchangeguy on 2007-03-29
complex number, if you'll notice from the users other posts, he says he has no panels, no icons, nothing. so please explain how he is supposed to "fire up a terminal". i'm thinking try reinstalling, and check the cd for errors, before you proceed with the install.

---

### Post by Benjamin Poulton on 2007-03-29
already checked for errors. CD seems good.

---

### Post by oilchangeguy on 2007-03-29
did it work corectly when you ran from the live cd?

---

### Post by Benjamin Poulton on 2007-03-29
I only have the alternate install CD

---

### Post by oilchangeguy on 2007-03-29
why are you using the alt cd? i suggest download and burn a normal copy of 6.10. or better yet 6.06, since it's going to be supported longer than 6.10. 2009 instead of 2008.

---

### Post by Benjamin Poulton on 2007-03-29
That was the CD that was recommended to me. I will try downloading a standard version. thanx for the help anyways.

---

### Post by ComplexNumber on 2007-03-29
**Benjamin Poulton**
what happens when you boot into failsafe from the boot menu, then type in 'startx' after you've logged in?

---

