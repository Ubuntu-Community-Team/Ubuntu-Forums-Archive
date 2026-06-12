---
title: "Kubuntu newbie problems [touchpad, boot issues]"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by warispeace on 2008-01-17
Hello,

I'm a new Linux user trying to get my laptop set up.  It's a Latitude D400.  I'm installing Kubuntu with KDE 4.  One thing I've had trouble with is disabling the touchpad tapping.  I could disable it in Gnome, but I don't see any option for that in the KDE settings.  I've looked online, but none of the fixes seem to work.  The synaptics drivers don't seem to be compatible with my hardware.

Also, I tried messing around with the graphics settings and it seemed to work fine, but after rebooting now I have a blank desktop.  As soon as I log in everything goes black, and the only thing I can see is the cursor.  Is there some way to restore the system defaults without having to reinstall?

Thanks all,

---

### Post by aun on 2008-01-18
As for the touchpad, this isn't an answer directly, but if you go to:

Startmenu > System Settings > Mouse > General

and select "Double-click to open files and folders (select icons on first click)", you may solve the tendency to open something every time you touch the pad.  If you are a (soon to be) ex Windows user you will find this much more natural feeling.

As for the second question, do you know what graphics settings you changed?  If I am understanding, you get the login screen, and everything goes black after that?  If so, it sounds like only your personal display settings are messed up, rather than system wide settings.  These are probably stored somewhere in /home/yourname/.kde/share, but I wouldn't really venture a guess without more info.  (I wouldn't play around with these too much unless you know what you are changing).

If it looks like you will have to reinstall, one thing you could try first is simply to move the entire contents of your home folder (including hidden files! those starting with a dot) to a sub-directory (or delete them or put them somewhere else), and let everything get recreated as you use it.  Mind you, I would consider this a last resort before a reinstall, but it might work.

---

