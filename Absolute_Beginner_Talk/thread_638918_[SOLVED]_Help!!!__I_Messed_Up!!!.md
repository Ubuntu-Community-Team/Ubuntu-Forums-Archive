---
title: "[SOLVED] Help!!!  I Messed Up!!!"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-12-12
Okay, I know it is just par for the course with me, but I seemed to have messed something up quite badly and for the life of me can't figure it out.

I had this "wise" idea yesterday to see if compiz fusion desktop effects would run on my PC and video card (obviously not - it loaded the old restricted driver for nvidia).  After a mess, I ran synaptic and removed everything that had to do with compiz and emerald.  Now the problems really began.  My display was all messed up - horz and vert sizes all screwed up.  So I ran the reconfigure of xserver-xorg, but it didn't help.  I looked at xorg.conf, and changed the "nvidia" just back to "nv" and tried again - still messed up.  So I edited it again and changed it to vesa and left the freq. as it was from the reconfigure of xserver (I selected the "medium" settings there for frequencies), and made 1200x1024 (?) the only resolution on the mode line.  Still messed up.

So I get to thinking (again, dangerous for me!) maybe there is something in my home folder that sets some kind of default for me.  You see, the login screen was okay, but then it screwed up after accepting my login.  So I created a new user.  Well, the desktop seems sized right with it, but any applications I run don't seem to know what size the screen is.  They start small, and have no upper-right icon for making them maximized.  I go through "view" and select full screen and 1 of 2 things happen:  the window remains tiny but the scroll bars disapear, or it maximizes to where it overflows the entire desktop.  In addition, non of the windows have the id bar at the top so I can't click on them and move them around, etc..

I'm sure I hosed something pretty good, but is there a way to recover from this without completely reinstalling Ubuntu??  BTW - I'm on Gutsy.

Thanks for any help!!

---

### Post by meborc on 2007-12-12
i would do **sudo apt-get install ubuntu-desktop** just to be sure you didn't remove something that shouldn't be removed...

the **sudo dpkg-reconfigure xserver-xorg** *should* work, if you choose the correct driver and resolution... tip: in the monitor selection, choose the middle level... then you can choose the default/best resolution and refresh rate for your monitor... the advanced level might be too complicated to insert correctly

---

### Post by spydon on 2007-12-12
You can also try to boot from a live cd and copy the xorg file when it's running and then replace your old xorg on the harddrive with the one from the live cd.

---

### Post by anewguy on 2007-12-12
> **meborc said:**
> i would do **sudo apt-get install ubuntu-desktop** just to be sure you didn't remove something that shouldn't be removed...

the **sudo dpkg-reconfigure xserver-xorg** *should* work, if you choose the correct driver and resolution... tip: in the monitor selection, choose the middle level... then you can choose the default/best resolution and refresh rate for your monitor... the advanced level might be too complicated to insert correctly

Tried your suggestion, but it said it what all installed.  However, you got me thinking.  Since I'm running Gutsy, I knew that some form of desktop effects gets delivered automatically when you install Gutsy.  So I went looking in synaptic, and sure enough there is one package called compiz-gnome (I think that's the name).  I reinstalled it and my windows started behaving again.  Then it allowed me to set the screen resolution for once and everything seems back to normal.  Thanks for the suggestion - it got me thinking!:)

---

