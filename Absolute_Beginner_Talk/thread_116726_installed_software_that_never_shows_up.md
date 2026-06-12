---
title: "installed software that never shows up"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by erikringmar on 2006-01-13
Hi there,

I have a basic and no doubt daft question: I have installed a lot of software that never shows up in the list of programmes -- some of them remain as bin files in /usr/bin, others are just gone somewhere.  Is there a general answer to this puzzle?

cheers,

Erik

---

### Post by aysiu on 2006-01-13
[QUOTE=erikringmar]
I have a basic and no doubt daft question: I have installed a lot of software that never shows up in the list of programmes -- some of them remain as bin files in /usr/bin, others are just gone somewhere.  Is there a general answer to this puzzle?[/QUOTE] Yes. It depends on the program. Some programs come with a menu icon. Others don't.
Sometimes a ```
killall gnome-panel
``` will refresh the menu, and the program will appear. Other times you have to add a menu icon yourself.

---

### Post by erikringmar on 2006-01-13
Hi, 

great.  Thanks a lot.  I'll try that.  I'm in Kubuntu -- does that make a difference?

cheers,

Erik

---

### Post by aysiu on 2006-01-13
[QUOTE=erikringmar]Hi, 

great.  Thanks a lot.  I'll try that.  I'm in Kubuntu -- does that make a difference?

cheers,

Erik[/QUOTE] Same principle applies in Kubuntu... you just don't do ```
killall gnome-panel
``` I'm not sure what the command is to refresh the KMenu.

---

### Post by poiuytr on 2006-01-13
I posted an answer to someone else's question ("Can't see Installed packages") which may help you, if you do need to go ahead and create a menu item.  Other folks posted on that topic, too.

Some of the specifics may be a little different for Kubuntu, however.

I know that there are a LOT of topics on this great web site, and searching through them can be a little unwieldy, but if you do search vigorously you may find answers to your questions already posted.

Anyway, here are my adding-to-the-menu hints, FWIW.  I hope it can help you, or someone else.  (Scroll down through the messages).  Try going to:

[http://ubuntuforums.org/showthread.php?t=115587](http://ubuntuforums.org/showthread.php?t=115587)

---

### Post by Mr_Grieves on 2006-01-13
A package that helps one to keep track on programs abit better:
[https://wiki.ubuntu.com/forum/software/CheckInstall](https://wiki.ubuntu.com/forum/software/CheckInstall)

---

