---
title: "Ubuntu boots successfully only a fraction of the time"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by level5music on 2007-12-28
Pretty much what it says.  My Gutsy install always lacked a splash screen, but sometimes ubuntu will freeze before it successfully boots.  I can actually tell by my monitor.  When the light on it is blue, it's "on".  When the light is yellow, it's "idle".  On a successful boot, the light will go from blue, to yellow for about 3 seconds, and then to blue followed immidiately by the login screen.

If it stays yellow, I'm in for a reboot.  Any reason why this occurs?  I'm sort of stuck in "quiet" boot mode.  If I try to edit grub from it's main menu before boot, my PC will restart rather than going to Ubuntu.  Thoughts?

---

### Post by Fixman on 2007-12-28
> **level5music said:**
> Pretty much what it says.  My Gutsy install always lacked a splash screen, but sometimes ubuntu will freeze before it successfully boots.  I can actually tell by my monitor.  When the light on it is blue, it's "on".  When the light is yellow, it's "idle".  On a successful boot, the light will go from blue, to yellow for about 3 seconds, and then to blue followed immidiately by the login screen.

If it stays yellow, I'm in for a reboot.  Any reason why this occurs?  I'm sort of stuck in "quiet" boot mode.  If I try to edit grub from it's main menu before boot, my PC will restart rather than going to Ubuntu.  Thoughts?

I have exacly the same problem, and its pretty anoying having to reboot and wait for Ubuntu to load like 6 or 7 times each time I open the computer.

HINT: edit /boot/grub/menu.lst file, seek for the Ubuntu entry, and add "splash" at the end of the root line.

---

### Post by rfruth on 2007-12-28
And AFTER you edit menu.lst can you tell where GG hangs (may have to cycle power on the monitor to get video back)

---

### Post by level5music on 2007-12-29
> **Fixman said:**
> I have exacly the same problem, and its pretty anoying having to reboot and wait for Ubuntu to load like 6 or 7 times each time I open the computer.

HINT: edit /boot/grub/menu.lst file, seek for the Ubuntu entry, and add "splash" at the end of the root line.

I've tried editing the grub at boot, trying to add splash or remove quiet, but if I do this, my machine will automatically reboot immidiately after keying "b".  Would editing the menu.lst file break my grub?

---

### Post by AmericanYellow on 2007-12-29
I have the same problem with my HP Pavillion zv6000. I never really found a "fix" but I noticed something weird  and unexplainable that works for me.

In my case, I press Alt+F1 once I reach where the splash screen should be. I see the different components being loaded after pressing the key combination. If I don't press Alt+F1 within a certain amount of time after the grub screen passes, my boot hangs and I have to restart my PC and try again (i've timed about 7-15 secs to press Alt+F1 before my PC hangs). This works every time for me and I've gotten use to it now.

Another thing I've noticed in my case is that my boot also hangs when I have something plugged in via USB during the boot. I use to use a USB mouse with my HP laptop and leaving it in caused my boot to hang when my system was loading the hardware components. I have to unplug the mouse and plug it back in after the boot. This was annoying so I completely stopped using the mouse.

I've been looking for a fix for months and no luck. Hopefully, my unexplainable finding will work for you. I know how frustrating this problem is...I installed Ubuntu and took my laptop to class the next day without testing after installing.  It didn't boot at all (tried throughout class), I couldn't take notes,  and had to reinstall Windows after class till I could get Ubuntu to boot. :mad:

---

