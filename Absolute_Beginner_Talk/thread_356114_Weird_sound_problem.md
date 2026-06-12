---
title: "Weird sound problem"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-08
Hi guys!  I am currently having two problems with my sound.  First of all, the buttons on my keyboard that are meant to control the sound are interfaced correctly with Ubuntu, but Ubuntu simply cannot change the volume (even if I go into the menus, the volume will look like it has changed but nothing happens).  It may be worth noting that I have an HP monitor with the speakers built in.

Second, there is a very loud scratching sound in the background when I play Battle for Wesnoth.  Are these things somehow related?

---

### Post by DSn0wMan on 2007-02-08
Try going int the preferences on the on the volume controll

In Gnome... right click the speaker icon, and select preferences

In KDE.... right click the speaker icon, and select Master Chanel

Try selecting PCM, or Phone/Headphones.

If this gives you the desired results you might be experiencing a driver bug. Check out this thread on launchpad.

[https://launchpad.net/ubuntu/+source....15/+bug/41015](https://launchpad.net/ubuntu/+source....15/+bug/41015)

---

### Post by orb9220 on 2007-02-08
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by Darklighter137 on 2007-02-08
That didn't do it, but apparently some set of sound options under "OSS Mixer" do the trick.  Is there any way to map my keyboard to that instead of whatever it is currently going to?

Thanks!

---

### Post by m0rph on 2007-02-08
Have you tried
System>>>>Preferences>>>>Keyboard Shortcuts 
:idea:

---

### Post by Darklighter137 on 2007-02-08
Thank you, but that didn't offer any option for linking the key press to the different sound module.  =(

---

