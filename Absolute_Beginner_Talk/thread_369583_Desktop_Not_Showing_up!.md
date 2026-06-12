---
title: "Desktop Not Showing up!"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by zombiepkx on 2007-02-24
My Desktop isn't showing up after boot, (No Icons, No Background, No Right Clicking on it.)

No clue why.


**ISSUE RESOLVED!!!**
I went into session manager, and found that Beryl-Manager was loading up, even though I have neither Beryl, nor XGL on this system anymore.
I disabled it, restarted XServer, and I'm back in the game.

Thanks to everyone for their input!

---

### Post by n8bounds on 2007-02-24
But you logged in thru GDM just fine?  I assume the live cd worked fine or did you install from an alternate?

---

### Post by zombiepkx on 2007-02-24
I've had my linux running for ages,
It just suddenly stopped working.
I boot through GDM, I have XFCE and Gnome on this, Gnome as default session, has been this way for a while, but I logged on today, and bam, no desktop.

---

### Post by haricharan on 2007-02-24
try pressing Ctrl+Alt+F6, login and use 
```
/etc/init.d/gdm restart
```
do you see any error messages while gdm restarts? or does it start fine?

---

### Post by zombiepkx on 2007-02-24
It starts just fine..

"Starting GDM..."                                    [ok]

---

### Post by n8bounds on 2007-02-24
And by "just fine" you mean no error messages but no GUI afterwards either, i.e. problem not solved, right?

Look at the /var/log/Xorg.somethingelsefile (you'll spot it) for xserver related errors.

(From one of your other tty terminals do a 
```

nano /var/log/X 
(once you have the X typed in hit TAB to ask BASH to finish the filename for you...it may present you with a few options if you keep hitting it, help it guess what you what by continuing to type out the filename)

```

Alternatively, you could boot the live cd and mount your root hard drive partition and view the file with gedit or something...

---

### Post by zombiepkx on 2007-02-25
No, it immediately restarts the Xserver (Or does an operation quite similar XD) And brings me to my nVidia Splash Screen, then my Login Screen.


No errors, nothing. It runs fine. Just no Desktop Background or Icons.

Edit: I just checked the logs, the only errors were attempting to connect to Wacom Devices (Meaning, basically nothing.)

But something that may mean something:
Could not init font path element /usr/share/fonts/X11/TTF, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID, removing from list!

---

### Post by zombiepkx on 2007-02-25
Bump

---

### Post by zombiepkx on 2007-02-25
bump2 Sorry guys, I REALLY want to fix this. 
I just found out that if I go to preferences > Desktop I can set a desktop image, but when I next boot up, it's gone. But I can keep setting it.

---

### Post by Keweenaw on 2007-12-31
Same problem here.  On each logout/login, the desktop is black instead of my background image.  All the items in my ~/Desktop/ folder do not show up on the desktop.

I think this has to do with one of the more recent updates, but have no idea which one.

---

### Post by jmauld on 2008-01-01
I've got this same problem.  Is there a fix for it?   It seemed to happen after the last round of software updates.

---

