---
title: "Stuck in Terminal!!"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-12
Somehow I messed things up so when I reboot the computer it doesn't come up in the login screen, it comes up in a black screen that says "home login", resembling the terminal.  Please help me get back to the login screen so I can get back to a GUI.
Thanks.

---

### Post by aysiu on 2006-05-12
Do you normally use KDE or Gnome?

---

### Post by yangiva on 2006-05-12
Have you tried to login with a user account and type, startx

---

### Post by brady618 on 2006-05-12
Kde

---

### Post by Sutekh on 2006-05-12
Have you tried replacing the busted xorg.conf?

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` 
If so, login at the Terminal and use
```
sudo /etc/init.d/kdm restart
``` Does this bring up the login screen?

```
startx
``` will also work, but should go straight to the desktop, rather than the login screen.

---

### Post by aysiu on 2006-05-12
Log in and try typing ```
sudo /etc/init.d/kdm restart
```

---

### Post by Clay85 on 2006-05-12
Did you try Alt+F7? I'm not sure if that works at bootup, but that's how to get out of the terminal when you're logged in. :-/

EDIT: I don't really know what I'm talking about, so just ignore me.

---

### Post by brady618 on 2006-05-12
Ok, I replaced the busted xorg.conf and tried sudo /etc/init.d/kdm restart, and this is what I get:

Stopping K Display Manager: kdm not running (/var/run/kdm.pid not found).
Not starting K Display Manager (kdm); it is not the default display manager.

When I do startx it puts me in my gnome desktop, but when I log out I'm still in the terminal.  How can I change this?  I miss my KDE and XFCE desktops.

---

### Post by Sutekh on 2006-05-12
Which did you install first?  KDE or XFCE?

If you installed XFCE first then the display manager is actually the GDM (GNOME display manager) not the KDM (KDE display manager), as Xubuntu uses the GDM for graphical log in.

```
sudo /etc/init.d/**gdm** restart
```

---

### Post by aysiu on 2006-05-12
You could always make KDM your default display manager: ```
sudo nano /etc/X11/default-display-manager
``` Change it from /usr/sbin/gdm to /usr/bin/kdm

---

### Post by brady618 on 2006-05-12
I did install Gnome first, but:

mike@Home:~$ sudo /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ ok ]
 * Not starting GNOME Display Manager (gdm); it is not the default display manager.

---

### Post by brady618 on 2006-05-12
I did sudo nano /etc/X11/default-display-manager, now where do I find  /usr/sbin/gdm??  I looked thru the entire screen, and went all the way to the bottom of the file.

---

### Post by aysiu on 2006-05-12
Well, first of all, keep in mind that Linux files and folders are case-sensitive: it's /etc/X11/default-display-manager, not /etc/x11/default-display-manager.

If you're sure you did X11 (and not x11), then the only thing in that file should be a line that says: ```
/usr/bin/kdm
``` There's nothing else in that file.

---

### Post by Sutekh on 2006-05-12
Another way to set the GDM or KDM as default is to use
```

sudo dpkg-reconfigure gdm
``` ```
sudo dpkg-reconfigure kdm
```

---

### Post by brady618 on 2006-05-12
Thank God!!  Everything is back to normal, and my Xubuntu desktop is back in working order as well.  Thank you all for your fantastic help!

---

### Post by Sutekh on 2006-05-12
Phew!!  Sorry about the wild goose chase for the eye candy!

The problem was I told you too much information. Those extra lines "RenderAccel" and "AllowGLXWithComposite" are only if you have 3D and acclerated graphics. With your integrated Intel graphics, that's probably not the case yet. My fault!

You can, if you are still willing to try, enable the Xubuntu compositor, but all you need is the "Composite" "Enable" part, not the rest of it. 

No hard feelings if you don't really feel like trying again!!

---

### Post by brady618 on 2006-05-12
It's no problem.  It really was a good learning experience.  I don't wanna do this thing halfa$$ed at all, I really wanna understand it all, it's just gunna take time and effort.  But anyway, what will the composite enable do?  Will I be able to get a transparent toolbar, similar to that in kde?

---

### Post by Sutekh on 2006-05-12
Yeah its pretty much the same thing.  The only difference is the KDE's composite manager (handles the transparency) can be turned on in the GUI.   XFCE's composite manager needs to be turned on with those composite enable lines.

---

### Post by brady618 on 2006-05-12
Ok Sutekh,

I guess I'm a bit too ambitious, cuz I tried it again with just the last code like you said, and it messed up my computer again, so I think I'm gunna leave it alone for now.  Oh who am I kidding, I'm sure I'll be trying it at least once more in the next 24 hrs.  But anyway, thanks for all the help/suggestions.

Peace

---

### Post by brady618 on 2006-05-12
BTW, perhaps the problem is that I have Drapper and it's not supported yet?  Or maybe it's cuz first I had Gnome, then Kde, and now Xfce?  Whatever.  Thanks again.

---

### Post by Sutekh on 2006-05-12
Ok, fair enough.  I am only using Dapper now, so I don't think it's that.  It's probably something small I overlooked.  The XFCE web-page makes it seem very easy though.  

[XFCE.org - How do I enable panel transparency and windows shadows?](http://www.xfce.org/index.php?page=documentation&lang=en#xcomposite)

It's never been a problem on my desktop (NVIDIA), so I am going to have to try it myself on my Laptop, which is Intel powered and see why its not working.

---

