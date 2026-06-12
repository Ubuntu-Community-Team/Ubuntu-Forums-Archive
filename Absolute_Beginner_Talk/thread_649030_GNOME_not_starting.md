---
title: "GNOME not starting"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by glaze0101 on 2007-12-24
I just installed a bunch of fonts into .fonts and right after that the system totally locked up.  So I did a hard restart (could not get into terminal) and when I did everything seems like it will load fine but after I enter my usr and pwd all I get is my wallpaper.

I am running 7.10 with both compiz-fusion and awn running.  I am thinking it might be something to do with the effects.  How do I turn off the effects through terminal so that I can load gnome without the effects?

Or does anyone have any other ideas??

-glaze

---

### Post by glaze0101 on 2007-12-24
bump.

---

### Post by LowSky on 2007-12-24
try booting into recovery mode, login, then type the command ```
startx
```

---

### Post by glaze0101 on 2007-12-24
Ok, that changed the screen to a blankish screen with an X in the middle then returned to the command line and said:

waiting for X server to shut down (EE) intel (0): I830 Vblank Pipe Setup Failed 0 
(EE) intel (0): I830 Vblank Pipe Setup Failed 0
(EE) intel (0): I830 Vblank Pipe Setup Failed 0
.FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1;fixing.


I rebooted and still only see my wallpaper.

I am sure that it is this free font path issue.  Any thoughts on what to do now?

---

### Post by LowSky on 2007-12-24
how did you install the fonts?

maybe you should put in a live cd and copy the cd's version of  /usr/share/fonts/X11/misc  over your installed version... it might fix things

---

### Post by AndyCooll on 2007-12-24
When you are dropped back into the command line (or alternatively choose ALT+F1 etc), you could also always try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Accept the defaults and hopefully that will put back in place original settings.

:cool:

---

### Post by Dropknee on 2007-12-31
This happen to me too, I write the user/pass then try to load gnome but the only thing I got is the wallpaper and the cursor, nothing else. I already fo the dpkg-reconfigure xserver-xorg but nothing happen and I know this problem is somethng with compiz, but I don't know how to fix it.

Any help???

Thanks

---

### Post by kjmathew on 2008-01-25
I too had this problem and the suspect gdm (Genome Display Manager) logs in** /var/log/gdm** were showing:
	[INDENT][B](EE) intel (0): I830 Vblank Pipe Setup Failed 0
	(EE) intel (0): I830 Vblank Pipe Setup Failed 0
	.FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1;fixing.[/B][/INDENT]
The logs were misleading but finally this worked for me:
(1) Either boot into recovery mode and login as root. Or when the screen is 'blankish' go to *virtual terminal 1* using Ctrl+Alt+F1 and login.
(2) Run **ps -Al | grep Xorg** to view the PID of any Xorg xserver process.
(3) Kill any Xorg process using [sudo] **kill -9 *<PID>*** (This kills gdm which would have been repeatedly trying to display the login screen, typically on the *virtual terminal 7* or tty7, try Ctrl+Alt+F7)
(4) Type the command **xinit**. This pops up an **xterm**inal window.
(5) Try running **gedit **or **firefox **or any other GUI application from the xterminal. The application should fail indicating the real problem.
(6) In my case, the error was that one of the quintessential shared libraries** libcairo.so** could not be found.
(7) I had just compiled and installed cairo on my PC. So I just had to run **ldconfig **and the problem was solved.

---

### Post by rakhi on 2008-02-26
> **kjmathew said:**
> I too had this problem and the suspect gdm (Genome Display Manager) logs in** /var/log/gdm** were showing:
	[INDENT][B](EE) intel (0): I830 Vblank Pipe Setup Failed 0
	(EE) intel (0): I830 Vblank Pipe Setup Failed 0
	.FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1;fixing.[/B][/INDENT]
The logs were misleading but finally this worked for me:
(1) Either boot into recovery mode and login as root. Or when the screen is 'blankish' go to *virtual terminal 1* using Ctrl+Alt+F1 and login.
(2) Run **ps -Al | grep Xorg** to view the PID of any Xorg xserver process.
(3) Kill any Xorg process using [sudo] **kill -9 *<PID>*** (This kills gdm which would have been repeatedly trying to display the login screen, typically on the *virtual terminal 7* or tty7, try Ctrl+Alt+F7)
(4) Type the command **xinit**. This pops up an **xterm**inal window.
(5) Try running **gedit **or **firefox **or any other GUI application from the xterminal. The application should fail indicating the real problem.
(6) In my case, the error was that one of the quintessential shared libraries** libcairo.so** could not be found.
(7) I had just compiled and installed cairo on my PC. So I just had to run **ldconfig **and the problem was solved.

Hi, I'm having exactly the same problem, only when I try opening GUI applications from the terminal everything seems to run just fine, so I'm still not sure what's wrong.  Any suggestions would be much appreciated!

---

### Post by Oldsoldier2003 on 2008-02-26
> **Dropknee said:**
> This happen to me too, I write the user/pass then try to load gnome but the only thing I got is the wallpaper and the cursor, nothing else. I already fo the dpkg-reconfigure xserver-xorg but nothing happen and I know this problem is somethng with compiz, but I don't know how to fix it.

Any help???

Thanks
if this happens alt+f2 run Nautilus and delete the .gnome directory in the users home. then alt + backspace or control +alt +backspace and when you relog gnome will display your icons and bars.

---

