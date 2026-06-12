---
title: "Takes minuthe tes for shutdown screen to pop up"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Bobtheknight on 2007-11-14
When I want to shut down my computer I click on system->quit.

But the problem is that it takes a long time before the shutdown panel will pop up.  I noticed there's a thread about this on development (gutsy gibbon) but that's closed.

[http://ubuntuforums.org/showthread.php?t=556194](http://ubuntuforums.org/showthread.php?t=556194)

Is there a solution to this now?

Thanks!

---

### Post by TidusBlade on 2007-11-14
try the shutdown command in the console/terminal ?

---

### Post by philinux on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)

Good reading eh.

---

### Post by Bobtheknight on 2007-11-14
The terminal works, and ctrl + alt + backspace and shutdown from there works also.  But the "quit" GUI doesn't work.

This is not system breaking, just annoying having to sit around for another 2 minutes waiting for shutdown window to appear.

So I guess issue is still not resolved.

---

### Post by kevinfishburne on 2008-03-02
This issue was also discussed [here]("http://ubuntuforums.org/showthread.php?t=556194") with no resolution.

I found that after disabling the two power management services under *System*, *Administration*, *Services* that this problem occurs. After reenabling the services the log off/shutdown screen appears immediately after I click the button.

Scratch all that... I spoke too soon. I'm troubleshooting it now and will post the resolution shortly...

I reenabled all services and session apps that were enabled by default, rebooted, and the problem was resolved. So, now it's a matter of narrowing down which app or apps cause the problem. Anyone want to help out? It's one or more of the following:

Under *Sessions*:
Bluetooth Manager
Evolution Alarm Notifier
Power Manager
Restricted Drivers Manager
Update Notifier
Visual

Under *Services*:
Actions scheduler (anacron)
Actions scheduler (atd)
Automated crash reports support (apport)
Bluetooth device management (bluetooth)
Computer activity logger (klogd)
Computer activity logger (sysklogd)
CPU Frequency manager (powernowd)
Power management (acpid)
Power management (apmd)

The machine I'm testing on is a Celeron 466 MHz, so I really don't feel like rebooting that many times.

---

### Post by Naipes on 2008-03-18
I think it's the **Power Manager** under *sessions*.

Check this out to automagically start the gnome power manager:

[http://www.gnome.org/projects/gnome-power-manager/faq.html#autostart](http://www.gnome.org/projects/gnome-power-manager/faq.html#autostart)

I had the same problem with the log out screen taking a long time to load.  I remembered I disabled the Power Manager because I'm working on a desktop and didn't think I needed to manage power.  However, when I re-enabled gnome power manager the "Hibernate" option reappeared in the log out screen AND the log out screen comes up much faster.

---

### Post by spacegypsy on 2008-07-06
Never had this issue before.

Now I installed Linux Mint Elyssa on my fathers desktop, and yep there it is.

I've been googling around and found that it is an old bug going back to Dapper. Unfortunately none of the remedy's seems to work for me and my father's desktop (Medion pentium 4 3.0GHz 512MB RAM ATI Radeon 9800 XL).

Any help?

---

### Post by forger on 2008-07-06
spacegypsy, you might want to post that at linuxmint: [http://linuxmint.com/forum/](http://linuxmint.com/forum/)

---

### Post by spacegypsy on 2008-07-06
I'll do.

---

