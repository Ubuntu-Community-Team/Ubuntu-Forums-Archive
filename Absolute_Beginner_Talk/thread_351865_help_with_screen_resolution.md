---
title: "help with screen resolution"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by bsunde on 2007-02-02
I have two questions.

How do I "bump down" my screen resolution from 1280x1024 (default) to 1024x768? Problem is, when I select that option in my drop down menu in Dapper, my monitor says "Input not supported," it blinks a bit and then I get logged off and I'm back at the login screen.   I've tried inputing the correct monitor specs in xorg.conf and I have tried using various drivers.  Currently, I have the vesa driver going because the ati driver won't work with my ATI Radeon 9100 and with fglrx I can't get Open Office to work.  Please help.

Second question.  I've been fiddling around a lot with my desktop setup.  Is there a way that I can get back to the original desktop that I had when I installed Dapper?  

Thanks!

---

### Post by aysiu on 2007-02-03
I don't know about the screen resolution thing, but what kind of "fiddling" are you talking about exactly, and are you using Ubuntu, Kubuntu, or Xubuntu?

---

### Post by ed-j on 2007-02-03
I sounds like you have a "non CRT" monitor, 19". If so, I think you are stuck with this resolution.
hope this helps.

---

### Post by ed-j on 2007-02-03
If you have been into the drivers in "xorg", I presume you have seen the Binary Drivers in Accessories>Add/Remove>System Tools? These would suit your ATI card.

---

### Post by bsunde on 2007-02-03
Ok.  I finally got this to work!  I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) for my ATI Radeon 9100 video card.  Now all my resolutions are supported and I get 3D acceleration.   

About the desktop...I'm using Ubuntu.  I just changed a lot of panel objects, sizing, fonts, icons...nothing major.  But if I could somewhat easily get back to the default desktop, that would be great.

---

### Post by igknighted on 2007-02-03
In system->preferences->themes set the them back to human and it should put everything back to default.

---

### Post by aysiu on 2007-02-03
Paste these commands into the terminal, then log out and log back in again: ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.gnome ~/.gnome.old
mv ~/.gnome2 ~/.gnome2.old
mv ~/.metacity ~/.metacity.old
mv ~/.themes ~/.themes.old
mv ~/.icons ~/.icons.old
mv ~/.nautilus ~/.nautilus.old
```

---

### Post by ed-j on 2007-02-03
> **bsunde said:**
> Ok.  I finally got this to work!  I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) for my ATI Radeon 9100 video card.  Now all my resolutions are supported and I get 3D acceleration.   

About the desktop...I'm using Ubuntu.  I just changed a lot of panel objects, sizing, fonts, icons...nothing major.  But if I could somewhat easily get back to the default desktop, that would be great.

Glad to hear you're sorted out! About the only thing I could add (perhaps) would be to right click on empty desktop to change choice of Backgound Preferences, and enter "Theme" through System Preferences to find "Human", the default Ubuntu theme. All the best.

---

