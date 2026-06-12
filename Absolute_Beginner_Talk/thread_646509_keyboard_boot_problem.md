---
title: "keyboard boot problem"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-12-21
hey all

when i boot into ubuntu im getting an annoying popup about my keyboard because X is expecting one setup and gnome has another and i have to choose one. this happens every boot up.  any idea how to sort this?

thanks 

alex

---

### Post by Tux.Ice on 2007-12-21
reinstall gutsy and make sure you select the right keyboard-

this should work

---

### Post by darkeale on 2007-12-21
well it did work ok until i installed 

sudo apt-get install xserver-xgl

to get compiz working, was hoping there would be another solution other than reinstalling

anymore suggestions?

---

### Post by Lord_Dicranius on 2007-12-21
I would leave a re-install as a last option...

What does "System -> Preferences -> Keyboard -> Layouts" show?  Also, check /etc/X11R6/xorg.conf and find the keyboard section ("Generic Keyboard").  What does that say?

---

### Post by darkeale on 2007-12-21
preferences > keyboard > layout shows

generic 101-key pc with United Kingdom layout

and /etc/X11R6/xorg.conf is empty, 

cheers

---

### Post by Lord_Dicranius on 2007-12-21
Checkout [this thread](http://ubuntuforums.org/showthread.php?t=612412).  Let us know if that helps :)

---

### Post by darkeale on 2007-12-21
yeah i tried that earlier but it didnt work. it seems like my computer as a whole is running slower too since this started which is a bit weird

---

### Post by Lord_Dicranius on 2007-12-21
Hmm, well to be honest, I'm stumped right now.  Wish I was in front of my laptop right now instead of my work machine which uses WinXP :(  Hopefully somebody else will chime in here.  I'll keep subscribed to the thread though, in case I come up with something.

---

### Post by darkeale on 2007-12-21
ok thanks for your help. im assuming the xorg file isnt meant to be empty?

---

### Post by Lord_Dicranius on 2007-12-21
Well, when helping another user with a keyboard issue (he was trying to switch to dvorak), I found [this post](http://ubuntuforums.org/showpost.php?p=142801&postcount=3) on the forum that helped him and mentioned that specific file.  I find it odd that yours is empty, but I can't say for sure whether that's part of your issue or not.

---

### Post by GGLucas on 2007-12-21
As far as I know, xorg.conf is in /etc/X11, not in /etc/X11R6, you could always do
```
locate xorg.conf
```
to find it.

Gnome is complaining that your keyboard layout is different in the gnome settings than what is in the xorg.conf file, change either of them to the other and it should stop (use the keyboard prefences menu for gnome, and just edit /etc/X11/xorg.conf (back it up first !) to change it for xorg), if you don't feel like editting xorg.conf manually, you could run
```
dpkg-reconfigure xserver-xorg
```
and select the correct keyboard layout from there, but it will ask you about all sorts of other things like graphics drivers and resolutions, and reset your xorg.conf to a generated default, erasing any changes you might have made manually.

---

### Post by darkeale on 2007-12-21
ok an update. looks like its gnome settings daemon thats the problem. i had to add this to the startup programs to get it to run on bootup, and since then thats when the problems start, when i disable it, my themes are not loaded properly but i dont get the keyboard error and everything runs way quicker. any ideas from that?

thanks 

alex.

ps all the keyboard stuff was in the /etc/X11/xorg,conf

---

