---
title: "[SOLVED] python 2.5 package messing up other apps"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-11-11
I upgraded to Gutsy, and...

this is me trying to open the compiz configuration manager

```
oliver@Profeten:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 24, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

trying to launch the screenlets gui thing

```
oliver@Profeten:~$ /usr/local/share/screenlets-manager/screenlets-manager.py > /dev/null
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 22, in <module>
    import gtk, gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

trying to open software sources manager

```
oliver@Profeten:~$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

I'm not sure how many apps are affected by this, but it's probably a lot. Just don't know how to fix it.

I realize this is a different issue, but resizing windows makes my fps drop to maybe 5 or so until I log out to gdm. Any thoughts there?

If you need more info, just tell me which and how to provide it :)

---

### Post by Nano Geek on 2007-11-12
Try reinstalling Python 2.4 and see if the problem persists. 
```
sudo apt-get install python2.4
```

---

### Post by OliverN on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> Try reinstalling Python 2.4 and see if the problem persists. 
```
sudo apt-get install python2.4
```

Do you mean Python 2.5? I tried reinstalling both Python 2.4 and Python 2.5 through Synaptic, but I still get the error.

---

### Post by Nano Geek on 2007-11-12
> **OliverN said:**
> Do you mean Python 2.5? I tried reinstalling both Python 2.4 and Python 2.5 through Synaptic, but I still get the error.You might want to try reinstalling Ubuntu then.

Just make sure you backup first.

---

### Post by Nano Geek on 2007-11-12
Or you could try reinstalling those programs just to see if it's some weird bug.

---

### Post by OliverN on 2007-11-13
> **asjdfwejqrfjcvm msz34rq33 said:**
> Or you could try reinstalling those programs just to see if it's some weird bug.

I tried reinstalling the apps, but no effect. Thank you for taking your time to help me, but I'd really rather not reinstall ubuntu completely because of this stupid error - I've been working for so long just to get everything to work, and now I'm just supposed to set it all back to basic? 

Please excuse me for asking and don't take it the wrong way, but are you suggesting a reinstall because of the knowledge you have on the issue or because you don't have anymore knowledge on the issue?

And if the first is the case could you elaborate on why a reinstall might be in order?

---

### Post by Nano Geek on 2007-11-14
> **OliverN said:**
> I tried reinstalling the apps, but no effect. Thank you for taking your time to help me, but I'd really rather not reinstall ubuntu completely because of this stupid error - I've been working for so long just to get everything to work, and now I'm just supposed to set it all back to basic? 

Please excuse me for asking and don't take it the wrong way, but are you suggesting a reinstall because of the knowledge you have on the issue or because you don't have anymore knowledge on the issue?

And if the first is the case could you elaborate on why a reinstall might be in order?Hey, Sorry it look so long for me to write back. Yes, the reason I suggested you reinstall is because I wasn't sure what else to do. This is one of the last things I can think of if you want to try it.```
sudo apt-get install python-cairo python-gtk-1.2 python-glade-1.2
```

---

### Post by Nano Geek on 2007-11-14
I just found this and it looks like it could solve your problem.
[https://bugs.launchpad.net/libcairo/+bug/129816/comments/11](https://bugs.launchpad.net/libcairo/+bug/129816/comments/11)
I hope it works.

---

### Post by OliverN on 2007-11-15
> **asjdfwejqrfjcvm msz34rq33 said:**
> I just found this and it looks like it could solve your problem.
[https://bugs.launchpad.net/libcairo/+bug/129816/comments/11](https://bugs.launchpad.net/libcairo/+bug/129816/comments/11)
I hope it works.

Sir, you have just become my personal hero. So painfully simple and yet so effective. Thank you so much for giving it a second shot. I think everything is in order now.

---

### Post by Nano Geek on 2007-11-15
> **OliverN said:**
> Sir, you have just become my personal hero. So painfully simple and yet so effective. Thank you so much for giving it a second shot. I think everything is in order now.I'm glad it worked for you. Enjoy! :KS

---

### Post by GregCwx1 on 2007-11-17
OliverN,

I'm wondering if the problem persists. I tried the fix with ldconfig after experiencing the same exact errors you reported. Problem is, the apps would usually work after a restart but then would stop working after awhile for no apparent reason. The crash reports are available in /var/crash and provide the details you were reporting earlier.

BTW, what do you have for files in usr/local/lib? I only had other directories like python2.5/ and something else. But no files! This is a frustrating bug in that it cannot always be repeated. I've been hunting for a solution for the past two days and this thread is the closest I've come to seeing someone with the same problem.

I upgraded to 7.10 from 7.04 by doing a complete clean install from the ALT - CD. I'm running gnome on a system76 laptop. I don't want to do a reinstall. BTW, I did have to turn on gusty backports and update to get sound to work on my system but I'm told the python problem is probably unrelated to that.

Any help would be appreciated! Thanks!

---

### Post by OliverN on 2007-11-21
> **GregCwx1 said:**
> OliverN,

I'm wondering if the problem persists. I tried the fix with ldconfig after experiencing the same exact errors you reported. Problem is, the apps would usually work after a restart but then would stop working after awhile for no apparent reason. The crash reports are available in /var/crash and provide the details you were reporting earlier.

BTW, what do you have for files in usr/local/lib? I only had other directories like python2.5/ and something else. But no files! This is a frustrating bug in that it cannot always be repeated. I've been hunting for a solution for the past two days and this thread is the closest I've come to seeing someone with the same problem.

I upgraded to 7.10 from 7.04 by doing a complete clean install from the ALT - CD. I'm running gnome on a system76 laptop. I don't want to do a reinstall. BTW, I did have to turn on gusty backports and update to get sound to work on my system but I'm told the python problem is probably unrelated to that.

Any help would be appreciated! Thanks!

The solution that ''asjdfwejqrfjcvm msz34rq33'' dug up still works for me, luckily. I haven't had any problems.

I'm sorry - I can't recall which files were in my usr/local/lib, but I do know that I simply deleted *everything* within the folder. My usr/local/lib folder is still completely empty, and I don't see any problems there.

I can imagine your frustration, I was quite surprised myself that I couldn't find a thread like this one. I don't know what more I can do for you, though. The reason I started this thread was that I had no idea what to do myself, so beyond the posted solution my mind is as blank as yours.

That you encounter this problem **from a clean install on a system76 laptop** completely amazes me, though. I'm running a Dell Inspiron 6400 laptop, and I upgraded directly from feisty to gutsy. Tell me if you need some more specific info on my system.

Wish I could help you more :-|

---

### Post by GregCwx1 on 2007-11-22
OliverN,

This recommendation from one of the System76 gurus seems to have fixed the problem:

```
sudo apt-get install -f #May fix broken dependencies

#Update any dependencies that were added
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

#Reload Python & GTK library
sudo apt-get --reinstall install python2.5 python-gtk2 python-pygtksourceview

sudo reboot
```

I thought I was back to stability with Gnome and was excited to start getting some work done.

Guess what? Not yet!

I was making changes to panels yesterday and tried to put the windows list applet on the top panel and it crahsed the gnome-panel! This was terribly disappointing! The one thing that has bugged me for awhile is that there is no easy way to save panel settings in the event a user ends up doing something stupid.

The bad thing is that even after a reboot, the panel crahed again immediately when logging into my account! The panel even crashed for my test user account when I tried to log in to that! What's the deal? You'd think the panel would be more stable across users. Anyway, I used the same process mentioned above and reinstalled the gnome-panel applet. I also removed all .gnome related settings directories from my /home account and restarted. What a pain. It's stable again. Question is: For how long?

I hope someone can share a similar experience so I know it is related to this distrib. 

Anyone out there found Kbuntu to be more stable? I may give KDE a try if Gnome keeps acting up on me.  ](*,)

Happy Turkey Day!

---

### Post by castoroil97 on 2008-03-29
woo hoo

I was getting the same error and this fix worked!!!

---

