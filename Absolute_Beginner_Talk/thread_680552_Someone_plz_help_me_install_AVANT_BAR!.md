---
title: "Someone plz help me install AVANT BAR!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-01-28
Ok i want to install this.. on to my ubuntu 7.10 this is the only thing i have trouble with installing...

[http://www.arsgeek.com/?p=2767](http://www.arsgeek.com/?p=2767) (i understand all the instruction)

Bu my question is.. I currently have a avan bar (look at my attachment) now, do i have Un-install it first?
If so... I have no clue how to do it... someone help me plz!

maybe anyone can suggest a diff or newer avant bar?

---

### Post by jonnywombat on 2008-01-28
Maybe I am missing something here but it seems to me that you have AWN installed already. 

It is not clear what you are trying to do.

---

### Post by yaknowwat on 2008-01-28
From the looks of it you already have it installed there are extensions for the bar to give it more than the special effects use a search engine for extensions.

---

### Post by angry_johnnie on 2008-01-28
Well, you already have it.  So, what's the difference?  Does the other one have more applets, like a cpu monitor, weather forecast and whatnot? If you want to replace it, then, yes.  You must uninstall the one you have, first.

This thread offers a complete howto on the subject:    [http://ubuntuforums.org/showthread.php?t=385981&highlight=stacks+avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=stacks+avant)

---

### Post by Bluestick on 2008-01-28
what im trying to do is install this [http://www.arsgeek.com/?p=2767](http://www.arsgeek.com/?p=2767)
cause it looks much better then the one i have! :)

 I just dont know how to remove that one i have first

oh that avant bar i got. it does not Auto hide so its really annoying... if i can just do that i would stick with one i have!

---

### Post by angry_johnnie on 2008-01-28
Hmm... how you're going to remove it is determined by how you installed it in the first place.  If you got it from synaptic package manager, or via apt-get, then you could just do:

sudo apt-get remove --purge avant-window-navigator

or, you could open synaptic, search for avant-window-navigator, click on it and mark for complete removal, and then click on apply.

As for auto-hiding, I don't think any version of awn is going to do that, although, to be honest, I'm really not sure.  Kiba-dock does, however, have an autohide function.

Here's the thread (on kiba-dock):

[http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock](http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock)

---

### Post by imaginal on 2008-01-28
For the reference, the new AWN does have autohide. (Just to keep you working towards the uninstall)

---

### Post by Bluestick on 2008-01-28
i just decided to stick with what i got... it took me a long time to install my current avant bar, i don't want to remove it, and then mess it all up... so anyway thx for the help guys i appreciated!

---

### Post by lswest on 2008-01-28
the picture on arsgeek is just AWN with a theme, and a few other extensions (such as the weather monitor) you can easily just add that to the installed AWN you have at the moment.  you can see what extensions you have installed by right-clicking your dock, choosing properties and going to extensions (i think) and there is a weather extension already added i think... and themes are in the properties menu under "themes".  a quick google search for "AWN dock themes" should bring up what you need^^

---

### Post by Bluestick on 2008-01-28
They thing is when i right click on my "Avant window navigator" and hit "preferences" Absolutely nothing happens any idea guys? 
 its been doing that since i installed it.

---

### Post by lswest on 2008-01-28
can you get to it from system-->preferences-->avant window manager ?(same preferences window)

if that doesn't work you can re-install avant in this way:
1) open a terminal and type ```
gksudo gedit /etc/apt/sources.list
```
2) append this: ```
## Avant Window Navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
``` to the end of that file
3) run ```
sudo apt-get install --reinstall avant-window-manager
```
4) try to get back into the preferences menu

---

### Post by Techwiz on 2008-01-28
> **Bluestick said:**
> what im trying to do is install this [http://www.arsgeek.com/?p=2767](http://www.arsgeek.com/?p=2767)
cause it looks much better then the one i have! :)

 I just dont know how to remove that one i have first

oh that avant bar i got. it does not Auto hide so its really annoying... if i can just do that i would stick with one i have!

You're looking for an AWN theme. Attached is a .tar.gz of most of them, Just unpack and put in a folder in your Home directory. Then in AWN preferences under System>Preferences>AWN manager (start awn first) Choose themes, then click add, and choose the theme you want from the list and click apply (after selecting theme to add to the list) And auto hide is in the AWN manager also.
Hope this helps!

---

