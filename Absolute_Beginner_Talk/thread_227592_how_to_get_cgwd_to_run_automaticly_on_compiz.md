---
title: "how to get cgwd to run automaticly on compiz?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-08-01
i cant seem to find the start up file for compiz...how can i make cgwd run automatically?
Thanks!

---

### Post by Dr. Nick on 2006-08-02
I just added 

cgwd --replace 

to system - prefrences - sessions -startup

---

### Post by Uncle Spellbinder on 2006-08-02
Had an update yesterday morning. Compiz Themer Cube in System Tray now has an option - Right click cube and you'll see a box to check, "Use cgwd".

---

### Post by jinxjinx on 2006-08-02
i dont think the first solution will work for me because some script is starting gnome-window-deco rater after cgwd. And I dont have a system tray...:(

---

### Post by Dr. Nick on 2006-08-02
if might work, the --replace option will  replace whatever the current window deceartor is

I have the sys tray and do not see the option to use cgwd though ??

---

### Post by Uncle Spellbinder on 2006-08-02
> **jinxjinx said:**
> i dont think the first solution will work for me because some script is starting gnome-window-deco rater after cgwd. And I dont have a system tray...:(

If you're running Ubuntu, Right click a blank area on your panel > click "add to panel" > scroll down to "Notification Area" > Click "Notification Area" once then click "add". It is now in your panel, This is your "system tray".

---

### Post by Uncle Spellbinder on 2006-08-02
> **Dr. Nick said:**
> I have the sys tray and do not see the option to use cgwd though ??

I was going to take a snapshot using "print screen" but I guess I can't with a menu open. Anyway. The last update I received had a Compiz update (I'm running xorg-aiglx + compiz [Quinn]). The "use cgwd" option was not there until after the update. I guess you could manually check for an update.

---

### Post by jinxjinx on 2006-08-02
i updated and added a notification area but i dont see an icon...

---

### Post by Dr. Nick on 2006-08-02
I just ran all my updates , no compiz one

Which ver do you have? mine is 0.3.3 according to the about button

---

### Post by Uncle Spellbinder on 2006-08-02
@ Dr. Nick

0.3.3. (gset-compiz) and Compiz Themer 0.22

---

### Post by Uncle Spellbinder on 2006-08-02
Oops - double post

---

### Post by Dr. Nick on 2006-08-02
weird, maybe its the way I have it launched then. My themes were not working so I sorta hacked up a solution, maybe my hack is getting in the way and is no longer needed

EDIT

Just disabled my 
cgwd --replace option and now my themes dont work and i lack the option to switch via gset-compiz thats odd. Guess I may mess with it tomorrow once I get some sleep

---

### Post by Uncle Spellbinder on 2006-08-02
I got print screen to work:

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/Compiz.png[/IMG]

---

### Post by _simon_ on 2006-08-02
Here's my menu.

I use this script

[http://www.compiz.net/viewtopic.php?pid=14922#p14922](http://www.compiz.net/viewtopic.php?pid=14922#p14922)

---

### Post by Uncle Spellbinder on 2006-08-02
In the beginning of my initial install of xorg-aiglx + compiz (Quinn) I was having problems theming. Went to the Compiz forums and found out (in my case) I had to replace my *#! /usr/bin/python* with the compiz-start.py from *WiLLiE's* post [here](http://www.compiz.net/viewtopic.php?pid=15059#p15059). Worked perfectly.

---

### Post by mcduck on 2006-08-02
> **jinxjinx said:**
> i dont think the first solution will work for me because some script is starting gnome-window-deco rater after cgwd. And I dont have a system tray...:(

just edit that script and replace gnome-window-decorator with cgwd ;)

---

### Post by jinxjinx on 2006-08-02
sure, but whats the name of the start up script?? i have nothing called compizstart or compizrs.py or compiz-start...
Thanks

---

### Post by Dr. Nick on 2006-08-02
The problem is this, theie are like 3-4 tutorials people are using and they all do things a bit differently :roll:


The name of the startup script will vary bewen which tutorial you have used.

The tutorial I used has compiz start.py, but the one I used before was called "thefuture" If you find out how you set it up origionally then you can find the name of the script. I may redo my setup and see if i can get teh "use cgwd" to work from gstet-compiz.

If you dont have gset-compiz you may be able to install it from synaptic.

---

### Post by Dr. Nick on 2006-08-03
simons link worked out.

Stupid me forgort to chmod it after moving it to /usr/bin ](*,) :roll:

Only thing about that script I dont like it it doesnt launch gset-compiz when clicking prefrences :(


I may expierment with others though now that I remember I have to chmod them

EDIT

Went back and got the script from post 27 on the above link and gset-compiz worked

---

