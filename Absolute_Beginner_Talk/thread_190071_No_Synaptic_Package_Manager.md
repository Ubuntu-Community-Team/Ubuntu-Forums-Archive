---
title: "No Synaptic Package Manager"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by JerryC on 2006-06-05
I booted from the CD and SPM was there.  I installed to the hard drive and everything came up OK except for two things.  When I explore in screensavers, the system locks up requiring a power off.  Don't care about that now; no one needs a ss in this day and age.  The other thing is Synaptic Package Manager doesn't appear anywhere in the menu.  It may be installed because on the first boot, Gnome automatically updated.  There are several other things in the administrative menu on CD boot that aren't there on the real installation menu.  Any ideas?

JC

---

### Post by %hMa@?b&lt;C on 2006-06-05
go to terminal and type
```
sudo synaptic
```
anything happen?

---

### Post by JerryC on 2006-06-05
Hey, Synaptic runs!  I thought it might be there.  Is it a pain to get it in the menu?

JC

---

### Post by catlett on 2006-06-05
Do you have "alacarte menu editor" installed under "applications" in the top panel. It will let you put synaptic in the menu, if it's not there.
If you have alacarte, look under "system" and then look in "administrative". Synaptic is there. If you don't have alacarte, call up synaptic from the terminal and instal alacarte with synaptic. You may have to restart for it to show up.

---

### Post by JerryC on 2006-06-05
I think I've figured out why a bunch of things don't show up in the admin menu.  When I figured out that my ID had been installed with root privledges, I went, like a good little linux user and changed my ID to remove root capability.  Now it won't let root sign in from the splash screen to change things back.  What is the graphical program to run from the command line that lets me change things back?

JC

---

### Post by catlett on 2006-06-05
System<Administrative<login window. The login window utility will allow you to change the preferences for login, including root being allowed to log in.

P.S. Just in case you don't remember. Hit on the "security" tab. Then check off  "allow local system administrator login" to allow root to login.

---

### Post by JerryC on 2006-06-05
OK.  I got it all fixed now.  (Except for the screensaver thing).  Thanks for the help everyone.

JC

---

