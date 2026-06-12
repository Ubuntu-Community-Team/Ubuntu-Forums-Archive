---
title: "How to switch between console and graphical mode"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-09-10
Hello.

I just wanted to know if there is some way to switch between console mode and graphical mode... I mean a bash shell command or something. I am using Xubuntu.

I'd like to know if I can type something in the shell to go to a console mode, then type something to go back to the desktop. Or if I can press some key at boot time, or something.
The idea is to make my server run in console mode, but have desktop avaliable when I want to easier make my tasks.

Thanks.

Jordi.

---

### Post by shoot2kill on 2006-09-10
CTRL + ALT + F1  = console

CTRL + ALT + F7  = Gnome/KDE Desktop

i am 99% sure of these shortcuts, but i not at an ubuntu PC

---

### Post by jordi_rc on 2006-09-11
Thanks shoot2kill, it also works in Xubuntu, that has Xfce desktop.

Nice help!

Jordi

---

### Post by Requiem on 2006-09-11
However your graphical server is still running, Go to System>Administration>Services and disable GDM.

now the graphical desktop won't start until you type "startx" thus saving cpu and ram for more important tasks

---

### Post by jordi_rc on 2006-09-11
Thanks Requiem.

So if I use the keys I don't free the resources??

If I do that disabling of GDM I do free the resources?

I practiced it, deactivated GDM, go to console, then typed "startx" and I was back to desktop. That was what I wanted. Thanks a lot, Requiem!

The only problem is that when I am back in the desktop and I try to restart the pc, I got this error:
"error in locking authority file: /home/jordi/.Xauthority"
What does this mean?

Anyway if I type reboot in console as root, it reboots. And I am back to desktop.

Jordi-

---

