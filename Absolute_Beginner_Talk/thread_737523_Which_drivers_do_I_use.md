---
title: "Which drivers do I use?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Spanky2k5 on 2008-03-27
Hey guys,
Just installed a Gutsy on a Compaq Presario 2500 (I'm new to Linux)
Got everything working but graphics aren't too brilliant (sluggish)

I wasn't expecting miracles but just wondered if anyone had any opinion on how to improve my graphics?
It's a Radeon IGP 330m/340m/350m using default ati driver

Thanks for any input!

---

### Post by JawsThemeSwimming428 on 2008-03-27
Did you install the Restricted Drivers?

---

### Post by Medieval_Creations on 2008-03-27
By using the Restricted Driver Manager, you should be able to install a different set of drivers, FGLRX. Which should significantly improve your vid-card's performance.

---

### Post by Spanky2k5 on 2008-03-27
When I click the Restricted Driver Manager I get a message saying 'Your Hardware Does Not Need Any Restricted Drivers'....Is there someway I can change that?

---

### Post by Medieval_Creations on 2008-03-27
Hmmm... I know that the driver that typically is needed is FGLRX, thats what I use on my Laptop with an ATI card.
but I'm not at home to check the specifics to walk you through installing the individual packages.

You could try Envy.  I've heard it has good HW detection.
Link: [http://albertomilone.com/index.html](http://albertomilone.com/index.html)

---

### Post by Spanky2k5 on 2008-03-27
I'll google it!

---

### Post by Spanky2k5 on 2008-03-27
ok I found xorg-driver-fglrx in Synaptic
I presume Install this and then maybe change driver through Screens & Graphics GUI?

EDIT: Already tried Envy, whenever I click Install Driver I get an Error and some log file

---

### Post by Spanky2k5 on 2008-03-27
Ok I changed to the flgrx driver, now Compiz doesn't wanna work and my windows don't have borders - also my cursor has changed to a black X

---

### Post by Spanky2k5 on 2008-03-27
Right now I've really ****** it, Ran the dpkg-configure thing because my display output changed to 640x480, as well as the other errors I mentioned in my previous post

Now my xserver fails to load

---

### Post by Medieval_Creations on 2008-03-27
It could be that the FGLRX driver doesn't support your vid card.

You should be able to change the driver back.
If you edit the file /etc/X11/xorg.conf there is a line in there that says
```
Driver "fglrx"
```

if you change that to ati you should be fine after restarting X or rebooting.

Also, Compiz is a resource hog.  After you get everything back up and running try disabeling it and see if that doesn't help.

---

### Post by Medieval_Creations on 2008-03-27
Also, after running the dpkg-reconfigure it probably saved a backup copy of your xorg file.  So you could try restoring one of those.

---

### Post by Spanky2k5 on 2008-03-27
I've sort of got it back up and running, I'm back with the ati driver but still don't have borders and my pointer is still a black cross.

Also when I right click on the desktop the menu that appears looks like a monitor running at an extremely high refresh rate might (i.e. heavily scrambled)

EDIT: Also I don't know how to disable Compiz! I think I'm running emerald as well though

---

### Post by Medieval_Creations on 2008-03-27
I've seen a fix for the no borders in Compiz, but since I don't use it I don't recall the steps.

You could try running the dpkg-reconfigure again... this time selecting ATI as the driver and letting it find all the other settings, like monitor and refresh rate.

See if it doesn't get you back to a fully working XServer.

---

### Post by Spanky2k5 on 2008-03-27
I gave that a go and I'm back in the xserver, just without borders, proper cursor etc...
This has happened to me before (although not with the scrambled menus and dodgy cursor) but I didn't fix it, it just stopped happening.

I've seen a few fixes to the border issue but as I'm running Xubuntu I think my menu is laid out differently to others

EDIT: any idea how I can manually change my refresh rate to 50hz rather than the 60 its currently on?

EDIT2: fglrx definately isn't the driver for these cards. Any ideas which one would be best? (Incl any manual edits I can make to config files?)

---

### Post by Medieval_Creations on 2008-03-27
> **Spanky2k5 said:**
> 
EDIT: any idea how I can manually change my refresh rate to 50hz rather than the 60 its currently on?

I've used GVDIM before and it's in the repositories.
It will give you a list of resolutions with refresh rates, so after a little trial and error you should be able to find one that works, if you don't know what your monitor supports.

---

