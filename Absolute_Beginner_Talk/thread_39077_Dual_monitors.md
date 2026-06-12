---
title: "Dual monitors"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by archiewood on 2005-06-03
Hi all,

Ubuntu just installed and xserver is working again, after I managed to screw it up after an aborted attempt at properly configuring it.

Can anyone give me advice on getting dual monitors to work please?  I noted during the xserver configuration that /etc/x11/xf86config-4 has to be manually edited to get the second head of a dual-head card to work, trouble is no such file exists in my install.  Help would be appreciated.

---

### Post by Leif on 2005-06-03
Search for twinview in the forums if you have one card with two outputs, or xinerama if you have two video cards. And since the upgrade to hoary the file you need to edit is /etc/X11/xorg.cong. I'll attach my setup for reference.

---

### Post by archiewood on 2005-06-20
[QUOTE=Leif]Search for twinview in the forums if you have one card with two outputs, or xinerama if you have two video cards. And since the upgrade to hoary the file you need to edit is /etc/X11/xorg.cong. I'll attach my setup for reference.[/QUOTE]
 Looking around it looks like twinview is for nvidia cards, mine is ati.  I ran fglrxconfig to see what kind of config file it produces, not thinking it would make any difference since it edits a different file to xorg.conf.  However it has worked, to a degree, but has produced a very peculiar setup I can't work with:

Both screens are working.
The desktop wraps to both screens correctly - the mouse can move left and right between them.  However:
Both screens are displaying the 'right' screen output.  Also, mouse clicks only register on the right screen.  Whenever I have tried running almost anything it has appeared on the 'left' screen so I basically can't do anything - I can't run a terminal, I can't run the file manager, I'm lucky Firefox has appeared on the right screen.  That also means I can't yet post my config files because I can't see them!

How do I stop xserver from running or quit to a command prompt, without the use of a terminal window?

---

### Post by Leif on 2005-06-20
I'm afraid since I don't have an ATI card I'm not too sure, but maybe this thread can help you :

[http://ubuntuforums.org/showthread.php?t=39062&highlight=ati+dual](http://ubuntuforums.org/showthread.php?t=39062&highlight=ati+dual)

Not perfect, but the conf files later on seem to work better than what you're reporting. To get a terminal, either use ctrl+alt+f1 (or any number up to 6) to login to another shell, and ctrl+alt+f7 to get back. To restart gnome, use ctrl+alt+backspace. If you do it a couple of times it will eventually crash.

---

### Post by archiewood on 2005-06-20
[QUOTE=Leif]I'm afraid since I don't have an ATI card I'm not too sure, but maybe this thread can help you :

[http://ubuntuforums.org/showthread.php?t=39062&highlight=ati+dual](http://ubuntuforums.org/showthread.php?t=39062&highlight=ati+dual)

Not perfect, but the conf files later on seem to work better than what you're reporting. To get a terminal, either use ctrl+alt+f1 (or any number up to 6) to login to another shell, and ctrl+alt+f7 to get back. To restart gnome, use ctrl+alt+backspace. If you do it a couple of times it will eventually crash.[/QUOTE]
 The problem isn't that I can't *open* a terminal, the problem is that when it does open it's on the left screen where I can't see it!  Same goes for the file browser.  The left screen is displaying the same as the right screen.  I think I have to fix the config file outside of gnome.  I guess I'll try to crash it then, thanks.

---

### Post by Leif on 2005-06-20
So when you use ctrl+alt+f1 it's not visible ? Because that should switch you out of graphical mode and cover all the screen. Alternatively, you can choose the recovery mode option at the boot screen so you don't boot into gnome.

---

### Post by archiewood on 2005-06-20
[QUOTE=Leif]So when you use ctrl+alt+f1 it's not visible ? Because that should switch you out of graphical mode and cover all the screen. Alternatively, you can choose the recovery mode option at the boot screen so you don't boot into gnome.[/QUOTE]
 crtl+alt+f1 didn't do anything as far as I could tell.  However once I figured out how to use the pseudo-desktop view in the taskbar (or whatever it's called in Linux) to find and drag the invisible windows into the visible screen I could run stuff as normal.  That thread helped a lot, I played around with the left/right settings until it worked, thanks for that!

---

