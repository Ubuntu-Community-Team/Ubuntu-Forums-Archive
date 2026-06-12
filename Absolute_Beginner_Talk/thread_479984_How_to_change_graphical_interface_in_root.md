---
title: "How to change graphical interface in root?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-06-20
[Note to mods: Wasn't sure where else to put this; if it belongs in a different category, feel free to move it.]

Hey there, I've got two IBM ThinkPad computers, one a A20m and the other a 390E. Both are currently installed with Dapper Drake 6.06. The A20m has a 12GB hard drive, and the 390E has a 6.5GB drive.

I want to be able to swap the drives in the laptops. I was initially able to do this, but after Ubuntu loaded and tried to activate the Gnome login menu, I got an error from X (?) saying that my graphical interface parameters didn't match what they were set to. I was able to view the errors, which I have no idea how to interpret, and then it turned off the GUI and ran Ubuntu in text-based mode. This happened with both laptops, of course.

I'm curious to know how to change the GUI parameters while in text mode so that I can make the swapped drives work without having to reinstall anything. Anyone know how to do this? :(

---

### Post by Happy_Man on 2007-06-20
It won't be fun... you'll be constantly dropped to a text mode.... but you can do it. Once you get to a prompt, type ```
sudo apt-get install lynx
sudo dpkg-reconfigure xserver-xorg
```

The first one is a text-based web browser... I recommend to everyone. The second command is what you need, though. Keep pressing enter until you get to a screen with a list of drivers. Scroll to highlight "vesa," spacebar to select, keep going until you exit. Now enter ```
/etc/init.d/gdm start
``` Hopefully, it will give you a login screen.

---

### Post by Halfling Rogue on 2007-06-20
> **Happy_Man said:**
> It won't be fun... you'll be constantly dropped to a text mode.... but you can do it.

Ah, Lynx. I remember that from Telnet days. But anyway, so there's no way to permanently reconfigure X, I'd have to do it every single time I logged in? Man. Might just reinstall it, then.

---

### Post by Halfling Rogue on 2007-06-21
Bumping for alternative options?

---

### Post by lazyart on 2007-06-21
every time you switch drives you would have to reconfigure.  If you only do it once then you set it and forget it.  You might have issues with other hardware because they are two different machines.  Good luck.

---

### Post by Halfling Rogue on 2007-06-21
So doing what Happy_Man said will keep it reconfigured until I swap them again? Awesome, that's just what I need. Thank you!

---

