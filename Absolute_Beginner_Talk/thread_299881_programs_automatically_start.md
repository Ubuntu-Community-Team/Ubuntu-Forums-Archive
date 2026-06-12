---
title: "programs automatically start"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-14
I am not sure what I did but every time I start ubuntu the session manager,amarok, and home folder automatically open.  How can I stop these?

---

### Post by That_Geek on 2006-11-14
go to system--> administration --> sessions

you will be able to change your startup programs

---

### Post by gentlemanmasher on 2006-11-14
My listed startup programs are as follows

update-notifier
/urs/lib/evolution/2.8/evolution-alarm-notify
gnome-power-manager
gnome volume manager --sm-disable
beagled



What is beagled?

---

### Post by 3rdalbum on 2006-11-14
Try the Current Session tab rather than the Startup Programs tab.

Beagled is a program that runs in the background and indexes your home directory. Unless your computer is going slowly, you should leave this running. (the Search function in Nautilus uses it)

---

### Post by d3v1ant_0n3 on 2006-11-14
If you didn't already spot it while looking in sessions, try unchecking 'Automatically save changes to session'. 

This will stop programs that you had open on logout from starting up again when you reboot.

---

### Post by gentlemanmasher on 2006-11-15
I have the save sessions button unchecked.  I also stopped the programs in current sessions but when I restart the same thing happens.

I have multiple desktops and it the programs don't start in KDE.

---

### Post by taurus on 2006-11-15
Go into Sessions again and delete the Default setting.

---

### Post by gentlemanmasher on 2006-11-15
I am at work will try when I get home and post thanks.

---

### Post by gentlemanmasher on 2006-11-15
That worked thanks for you help.

---

