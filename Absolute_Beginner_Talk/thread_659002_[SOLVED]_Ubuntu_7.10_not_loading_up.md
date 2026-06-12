---
title: "[SOLVED] Ubuntu 7.10 not loading up"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by fireboy129 on 2008-01-05
RAWR. another problem.

this time, its the fact that ubuntu wont let me log in. i enter my name and password, everything goes away on my screen, and i get what i have termed the "peach screen of death." its a peach colored screen that shows up after i enter my password. nothing is on it... its kinda like the BSOD w/ windows, but this one is just the natural background color @ the login screen.

please help. i want ubuntu!!

---

### Post by tgilber1 on 2008-01-05
Sound like you're booting up to Ubuntu, but you're having trouble loading GUI.  What kind of video card do you have and which driver are you using?

---

### Post by candtalan on 2008-01-05
what happens when you use a live ubuntu (7.10) cd? Does it boot ok and proceed to show a desktop display?

---

### Post by fireboy129 on 2008-01-05
yea it does... just finished installing and getting everything set up, and now it doesnt work!

---

### Post by rkd on 2008-01-05
You might be having the same problem being discussed in this thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=585635](http://ohioloco.ubuntuforums.org/showthread.php?t=585635)

Read through that thread and see whether it seems the same as your problem.  If not, come back here and tell us more about your problem.  If that other thread is the same as yours, it might be best to join in that discussion -- one of the guys is trying to collect log information from many people with the problem in the hope it will help him find the underlying cause of the problem.

---

### Post by candtalan on 2008-01-06
> **fireboy129 said:**
> yea it does... just finished installing and getting everything set up, and now it doesnt work!
It may be the video driver is wrongly identified or wrongly named in the installed situation - I have had that sometimes. To solve this, I used a live CD (which worked) and then looked at the file /etc/X11/xorg.conf to identify what name of video driver was used in the live cd (working) then arranged by other means to edit the installed file to change the driver name (only changed this, nothing else) to the name which obviously worked and then re started it from the hard drive. It worked ok then.
hth

---

### Post by jck99nz on 2008-01-06
If the peach screen hangs around for ever (and menu bars never appear) then you're probably experiencing the same issue described here [http://ohioloco.ubuntuforums.org/showthread.php?t=658843](http://ohioloco.ubuntuforums.org/showthread.php?t=658843) 

Briefly, clean install of Ubuntu results in working system; accepting the recommended updates (from the default enabled repositories) results in the 'peach screen of death' on rebooting. It's not possible to open a terminal, although the mouse pointer works and ctrl-alt-del brings up the shutdown menu. It's been reported by people with both ATI and Nvidia graphics cards. 

If you only install security updates (uncheck the recommended updates), then the problem doesn't occur. It's only been happening since around 1 Jan, so it seems to be caused by an update added since then. Anyone know how to order updates chronologically in the update manager window?

No one on the other topic discussion has come up with a solution yet.

---

### Post by fireboy129 on 2008-01-06
fixed!!!

yay.

---

### Post by jck99nz on 2008-01-06
How did you fix it? Did you have to reinstall ubuntu?

---

### Post by fireboy129 on 2008-01-07
actually, i wasnt loading GNOME. i was loading Xclient.

Xclient still doesnt work, but i use GNOME now.

10 second delay on GNOME.

---

