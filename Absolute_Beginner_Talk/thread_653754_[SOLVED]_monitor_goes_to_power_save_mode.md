---
title: "[SOLVED] monitor goes to power save mode"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by xodroolis on 2007-12-30
how do i set the monitor not to go to power save mode?
it turns to black after 5 minutes if the pc is idle and after 50 minutes as i set it switches off
how do i set no to turn black after 5 minutes?
it is really annoying while i watch a movie

---

### Post by cifdtruckie on 2007-12-30
Try going to Systen -> Preferences -> Power Management

There you can fiddle around with the power settings, such as how long it takes (if ever) for your computer to go into sleep mode.

---

### Post by chewearn on 2007-12-30
You can either set the movie player to prevent monitor blanking (some players support this), or you can set your desktop power management settings.

For Ubuntu Gnome, its at:
Top Panel Menu > System > Preferences > Power Management

Edit:
Rats!  Beaten to it:lolflag:

---

### Post by xodroolis on 2007-12-30
i ve set via the power management after 50 minutes the the dipslay to go to sleep.
The problem is that after 10 minutes after being idle the screen goes to black until i move the mouse again. 10 minutes! not 50 (after 50 it swithes off as i said, ok)
Any suggestions?

---

### Post by chewearn on 2007-12-31
> **xodroolis said:**
> i ve set via the power management after 50 minutes the the dipslay to go to sleep.
The problem is that after 10 minutes after being idle the screen goes to black until i move the mouse again. 10 minutes! not 50 (after 50 it swithes off as i said, ok)
Any suggestions?

How about the screensaver?  Did you have "blank screen" turned on?
System > preferences > Screensaver

---

### Post by Phurious on 2008-01-02
Not to hijack your thread, but I am experiencing something very similar.  I have my screensaver disabled, and power management set to never turn my display off, but that appears to have no effect.  My monitor will enter powersave mode after 10 minutes of inactivity regardless of these settings.  Also more bizarre and perhaps indicative of a power management issue:  When I first boot my machine, if I do not hit a key IMMEDIATELY after the logon screen appears, my monitor enters powersave mode.

:confused:

---

### Post by Linuxratty on 2008-01-02
> **Phurious said:**
> Not to hijack your thread, but I am experiencing something very similar.  I have my screensaver disabled, and power management set to never turn my display off, but that appears to have no effect.  My monitor will enter powersave mode after 10 minutes of inactivity regardless of these settings.  Also more bizarre and perhaps indicative of a power management issue:  When I first boot my machine, if I do not hit a key IMMEDIATELY after the logon screen appears, my monitor enters powersave mode.

:confused:
 I'm having the same problem..I also did what you did,but it stays the same and this happened on three different distros!
Just plane weird!

---

### Post by Enginirical on 2008-01-02
I had the same (unresolved) problem in feisty and now the same issue in Gutsy. All the power management settings are set to never and I had not selected screen saver either!

I found this, here: [http://ubuntuforums.org/archive/index.php/t-442190.html](http://ubuntuforums.org/archive/index.php/t-442190.html)

quote: Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

I tried it, and all I can say so far is that the graphics card still works. I will leave my laptop running tomorrow to see if it has cured the problem then let you guys know!

UPDATE: ok, well it seems to have resolved the screen blanking problem, however there are other weird things going on: I found in another post that this solution would mean you could not use the screensaver. Well the screensaver works still since I selected 1min idle to test it. But when I went back to uncheck or change the idle time, when clicking screensaver in system preferences it would suddenly log me out of the current session! The only way to stop it is to really quickly click on the screensaver window when it pops up which prevents ubuntu from logging me out of the current session. To be honest although not perfect but It´s a fair swap and I rather my screen stops blacking out.

---

### Post by xodroolis on 2008-01-03
Well... this is interesting... same problem to many of us.
i use fglrx on an ATI radeon 9600.
i dont know if i want to do what Enginirical did (whome i thank for the problem sharing). I will leave it as it is for now. or unless a more stable solution is proposed.

---

### Post by Linuxratty on 2008-01-03
> **xodroolis said:**
> Well... this is interesting... same problem to many of us.
i use fglrx on an ATI radeon 9600.
i dont know if i want to do what Enginirical did (whome i thank for the problem sharing). I will leave it as it is yet as it is now. unless a more stable solution is proposed.

 Being the insecure linux user that I am, I shall do the same.

---

### Post by Enginirical on 2008-01-07
It&#347; no problem if you always have a backup of xorg.conf file. In fact I had that problem before a restart. Since restart, everything works as it should including screen saver! 

Gutsy is far more stable than you think!

---

### Post by xodroolis on 2008-01-08
> **Enginirical said:**
> I had the same (unresolved) problem in feisty and now the same issue in Gutsy. All the power management settings are set to never and I had not selected screen saver either!

I found this, here: [http://ubuntuforums.org/archive/index.php/t-442190.html](http://ubuntuforums.org/archive/index.php/t-442190.html)

quote: Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

I tried it, and all I can say so far is that the graphics card still works. I will leave my laptop running tomorrow to see if it has cured the problem then let you guys know!

UPDATE: ok, well it seems to have resolved the screen blanking problem, however there are other weird things going on: I found in another post that this solution would mean you could not use the screensaver. Well the screensaver works still since I selected 1min idle to test it. But when I went back to uncheck or change the idle time, when clicking screensaver in system preferences it would suddenly log me out of the current session! The only way to stop it is to really quickly click on the screensaver window when it pops up which prevents ubuntu from logging me out of the current session. To be honest although not perfect but It´s a fair swap and I rather my screen stops blacking out.

Ok I did it! so far no problems... the screen doesnt turn to black neither it goes to power save. if i notice any stable problems i will notify you

---

### Post by Shazaam on 2008-01-08
What everyone is experiencing is related to DPMS (Display Power Management) which is linked to the Energy Star spec for electronic products. It is built in to almost ALL monitors so fiddling with the Linux power manager will have ZERO effect. But, it looks like that change to xorg.conf that Enginirical posted MAY work. I will have to try it out as I have the same problem.
The difference between Linux and Windows is that Windows reads the EDID (kind of like a bios for the monitor) from the monitor better than Linux.

---

