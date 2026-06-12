---
title: "xubuntu 8.04 g3 mac strange error"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by lobotheduck on 2008-06-22
I've installed ubuntu 8.04 server and installed xubuntu desktop on top.  I then did the xorg.conf edits so that it wont crash when it boots.  

When i rebooted it started as normal with the xubuntu login but upon logging in, all that was on screen was the desktop background and a console window.

Does anybody have any idea why it doesn't load the toolbars and whatnot or why it boots a console window in the first place?

Any help would be greatly appreciated :)

---

### Post by howlingmadhowie on 2008-06-22
is your system clock set to the right time? i know that gnome has a problem with the system clock pointing to strange dates. maybe xfce does too.

---

### Post by lobotheduck on 2008-06-22
Im pretty sure it is (typed "sudo clock" into console.  I'm pretty new to linux). 

That said i don't think that would be an issue as i previously had ubuntu 8.04 desktop installed and it was fine (a bit slow but thats why i resorted to xubuntu)

I can still run apps by typing them into the command line but i dont have the top/bottom menu's and whatnot.

---

### Post by stream303 on 2008-06-22
The one thing that concerns me about Xubuntu, is that they have not released an "official" release of Hardy - only a late-beta and then stopped.  I'm not sure if the xubuntu-desktop meta package is getting any updates.

Were you following this guide - even though the intro is about x86, it works for ppc just as well:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Unless Xubuntu follows through with a release or some sort of indication about Hardy updates, you might be better off running your own custom XFCE4 (which is what xubuntu is based on) and putting in xfce4 additions to your liking.

---

### Post by lobotheduck on 2008-06-22
Thanks, I never realized how customizable the graphical elements of ubuntu could be.

I think other people have installed xubuntu this way (from reading other threads) but if i can't get it working then I'll use that guide and do it that way.

Thanks for the insight :)

UPDATE!
I typed "xfce4-panel" and it launched the menus and everything, now all i need is to sort out the lack of workspaces, system options and that the programs are stuck to the top left of the screen and are immovable.

If anybody has any ideas or help then i would really appreciate it :)

---

### Post by lobotheduck on 2008-06-22
It's all sorted [link]("http://http://ubuntuforums.org/showthread.php?t=813089&page=2")

Thanks for the help everyone :D

---

### Post by stream303 on 2008-07-01
If you are running Hardy 8.04 and Xubuntu, or xfce4 and it doesn't seem to come up after the gdm login screen, check this file:

**/usr/share/xsessions/xfce4.desktop**

and check to see if the last line reads
```
Exec=xfce4-session
```

---

