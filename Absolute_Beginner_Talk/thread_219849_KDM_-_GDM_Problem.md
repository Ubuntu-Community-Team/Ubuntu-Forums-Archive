---
title: "KDM - GDM Problem"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-07-20
OK, so I thought I'd try the KDE Desktop. Though I do like it, I'm so use to the Gnome desktop/experience, I switched back. I now have the KDM starting instead of the GDM. I originally installed KDE this way: *sudo aptitude install kubuntu-desktop*. I removed it this way: *sudo aptitude remove kubuntu-desktop*. 

How do I get Gnome Desktop Manager back and remove KDM?

---

### Post by mattisking on 2006-07-20
There's almost certainly a better way than this, but since you have no other responses at this point:
I'd go into Synaptic and look at the dependencies for kubuntu-desktop and uninstall the most obvious packages. Remember that packages like ubuntu-desktop, kubuntu-desktop, xubuntu-desktop are just meta-packages that contain required packages. There are some packages in common with all of these, so uninstalling the meta package just can't uninstall all the dependant ones.

---

### Post by Uncle Spellbinder on 2006-07-20
Far too many dependencies for me to even guess at what to remove. No other way? Or am I stuck with reformating and re-installing Ubuntu Dapper?

---

### Post by Uncle Spellbinder on 2006-07-20
OK, I did *sudo aptitude remove kubuntu-desktop* again, rebooted. Now the KUBUNTU startup screen shows, but the Gnome login screen appears and I seem to log into Gnome as normal.  
 But when checking for updates (update manager), I get 

> Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.


Ideas??

---

### Post by Uncle Spellbinder on 2006-07-20
Logged out, rebooted and set Gnome as "default" session. No more warning when checking for updates. But I still have the Kubuntu startup screen instead of Ubuntu. :-k :???:

---

### Post by Jucato on 2006-07-20
This might be of help to you:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

Oh, and btw, GDM/KDM means GNOME/KDE *Display* Manager. Just thought you would like to know.

---

### Post by The Mekon on 2006-07-20
I believe the following [howto]("http://www.ubuntuforums.org/showthread.php?t=205002&highlight=ubuntu-desktop+packages") addresses this

---

### Post by Uncle Spellbinder on 2006-07-20
> **The Mekon said:**
> I believe the following [howto]("http://www.ubuntuforums.org/showthread.php?t=205002&highlight=ubuntu-desktop+packages") addresses this

THANKS!!!  That link (and sub-link) did it. I'm back to "pure Gnome". As much as I like the KDE look, there really is no substitute for the Gnome experience....IMHO.  :D

---

