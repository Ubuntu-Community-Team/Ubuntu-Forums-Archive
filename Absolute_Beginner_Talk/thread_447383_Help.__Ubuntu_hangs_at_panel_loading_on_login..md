---
title: "Help.  Ubuntu hangs at panel loading on login."
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-17
For some reason, when I boot Ubuntu and log into Gnome, the splash screen freezes at the loading panel stage.  The splash stays on screen, and the menus of the system are still responsive, but none of the startup programs load (beryl, **NetworkManager**, tomboy, glipper, power monitor, etc.).  

Oddly enough, if I wait about 5-10 minutes, the problem magically clears up, the Gnome splash screen disappears, and the startup programs jump to life.  But this is completely unacceptable behavior.  And it does this every time I reboot.

Earlier today I booted Ubuntu several times and it behaved normally, and this from one boot to the next it just started doing this out of nowhere.  And I can't think of anything I did during the last normal bootup that would have changed anything to make this happen.  I didn't install any new packages or change any configurations. 

Any ideas on what might be causing this problem and how to fix it?

---

### Post by n8bounds on 2007-05-17
beryl/compiz/desktop effects can sometimes do that to you, sounds like you are using beryl--does this happen when you Don't autoload beryl-manager or however you have it setup?

---

### Post by laptoplinux on 2007-05-18
I thought that too at first and tried disabling beryl at startup, but that didn't change anything.  Just to be safe, I think I will add a sleep timer to beryl at startup, though.

---

### Post by kxs on 2007-05-18
Something similar happens on my laptop. When I type login and password and hit enter ubuntu freezes. I have to move the mouse to make it work again. It happens frequently after upgrading to 7.04. I don`t have beryll. Didn`t install new programs. Just upgraded and it started to freeze sometime. Why is that?

---

### Post by whomever21 on 2007-07-06
Did the sleep timer help? I'm having the same issue.

---

