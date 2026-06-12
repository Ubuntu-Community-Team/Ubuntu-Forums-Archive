---
title: "Reliability"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Wolf1994 on 2005-11-20
I often heard that Unix-like systems are very reliable. But also heard that in hands of newbie it may become dangerous.

Questioin.

When I ran LiveCD, performed some aquintance actions and then ran ScreenSaver and pressed "Preview" - system halted (except mouse pointer). Why its happen? And what consequences may be possible in case - it was installed operation system?

---

### Post by Gadren on 2005-11-20
I'm not that experienced with Ubuntu, but I'd say that the reason for the freeze was because it was a LiveCD (and thus ran more slowly than an installed system would).  If such a thing did happen on an installation, then I'd say that it wouldn't do any damage, at least not any irreversible damage.

---

### Post by aysiu on 2005-11-20
Sounds to me as if you just ran out of RAM (or memory).

A live CD does not harm your hard drive unless you go out of your way to manually mount the hard drive as root and start messing around with it that way.

You have to understand, though--because the live CD does not touch your hard drive, it has to be run completely off the CD and RAM. That means it's not only using the RAM as RAM, but it's also using RAM to run the entire operating system that isn't on the disk. If you have 64 or 128 MB of RAM, it can be painfully slow to the point where it just freezes.

This wouldn't be the case with an actual installation, as the installation would use the hard drive for data and the operating system and use the RAM as RAM.

---

### Post by Kvark on 2005-11-20
[QUOTE=Wolf1994]But also heard that in hands of newbie it may become dangerous.[/QUOTE]
You normally don't have the power to mess up the system so don't worry. The only thing you can mess up is settings and files that belong to your user account. Whenever you do something that can change (or mess up) the system like install programs or edit a configuration file that affects other users too you will have to enter your password to gain permission to do it. Just think twice before doing something that requires your password.

[QUOTE=Wolf1994]I often heard that Unix-like systems are very reliable.[/QUOTE]
Ubuntu is a very stable and reliable system. But the countless programs that can run on Linux systems vary in quality of course. Don't be surpriced if you find a program is buggy, chrashes or freezes. But when a program does that it usually does not have any effect on the system or on other programs.

[QUOTE=Wolf1994]When I ran LiveCD, performed some aquintance actions and then ran ScreenSaver and pressed "Preview" - system halted (except mouse pointer).[/QUOTE]
Pressing the power button to reboot always works. A quicker way that solves almost all problems is to press Ctrl+Alt+Backspace, it will kill all graphical programs and restart the graphical environment.

If you wanted to do some advanced stuff to avoid losing unsaved work I bet you could have killed only the screensaver and kept going as if nothing happened. To do that press Ctrl+Alt+F1 and log in to the terminal. Use the commands "ps -a" or "top"  to figure out the exact name of the missbehaving program. Then type "killall badprogram". Lastly press Ctrl+Alt+F7 to get back to the graphical environment.

[QUOTE=Wolf1994]Why its happen? And what consequences may be possible in case - it was installed operation system?[/QUOTE]
The worst possible consequence of that would be to lose all unsaved work. It could perhaps have been an issue with graphics drivers. Was it a 3D screenaver? What graphics card do you have?

---

### Post by Wolf1994 on 2005-11-20
That's what I guessed. One thing what I in doubt about is that my PC's memory = 256 Mb that twice of neccessary memory.

---

### Post by Wolf1994 on 2005-11-20
> Was it a 3D screenaver? What graphics card do you have?
Yes - that's was 3D screensaver. My card: Radeon 9000

---

### Post by Kvark on 2005-11-20
[QUOTE=Wolf1994]Yes - that's was 3D screensaver. My card: Radeon 9000[/QUOTE]
Click on the "Up-to-date repositories" link in aysiu's signature and follow the instructions there.
Then fire up Synaptic Package Manager and install the package called "xorg-driver-fglrx". Follow the other link in aysiu's signature if you need help with how to use synaptic. I think this is one of the few changes that requires a restart of the graphical environment so hit Ctrl+Alt+Backspace when you've installed the drivers.

After that you'll have proper 3D accelleration drivers for your raedon card, which you want even if this wasn't the problem.

---

