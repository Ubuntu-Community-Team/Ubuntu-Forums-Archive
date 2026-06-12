---
title: "Can't Get into Ubuntu"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2006-12-26
Hello,
I just installed Ubuntu for the first time yesterday. I was up late bent on getting counter-strike to work right with wine and everything. The problem is that when I installed the Kubuntu-desktop so I could install XFree86, it didn't install right. Everytime when I boot (from the start), it boots to something that looks like DOS. It has me login and I can do terminal commands and that's it. I got XFree86 installed (that may be the problem) and I uninstalled Kubuntu (used "sudo aptitude remove kubuntu-desktop"). I made sure the ubuntu-desktop was installed ("sudo aptitude install ubuntu-desktop"). I boot up and I still get to the DOS looking place (what  is it called?) How to I return to the regular Ubuntu?
Thanks,
Mikael

P.S. I Have Ubuntu 6.10

---

### Post by halitech on 2006-12-26
from the command line (CLI) you can run startx and that should get you into a GUI but sounds like you need something like GDM installed (graphical desktop manager) so it will start automatically

---

### Post by Hendrixski on 2006-12-26
You probably see the Grub boot loader come up when you first turn on the computer and it give you the options of Ubuntu, Ubuntu safe mode, Windows, or other OS ...  make sure you're not turning onto safe mode, because that won't give you the graphical interface, it's only command line.

if you do get into safe mode, you can turn on the X11 server (that's the thing that makes your graphical stuff work) by typing the command "startx".  If that doesn't work then that means that X11 is crashing, which means you screwed up your xorg.conf file at some point.  Which.. you should have saved a backup copy of the orriginal if you made any changes to it, so just replace the current one with the orriginal and TADA, problem solved.  If not, keep posting here, we'll help you through this,

---

### Post by mikaelsnavy on 2006-12-26
Thanks for the quick reply, I tried it and it failed. I think that I need to use Kubuntu-Desktop instead so I can use Xfree86. Now I at least I know the command! 
Thanks A Lot,
Mikael

---

### Post by MkfIbK7a on 2006-12-26
try xinit

---

