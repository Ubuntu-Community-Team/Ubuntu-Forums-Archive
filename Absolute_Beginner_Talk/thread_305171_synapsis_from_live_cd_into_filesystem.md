---
title: "synapsis from live cd into filesystem"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Bobtheknight on 2006-11-22
Hey, I managed to break my xorg.conf, no, make that my graphics drivers by following a guide that calls for "go to synapsis and removing everything fglrx and restricted...something"  so I did that and tried to install the radeon driver and configure my xorg.conf which... didn't work.

Since I deleted my old drivers I can't go back.  So I am faced with the question: can I re-install stuff into my filesystem via synapsis from a live cd?

The stuff I want to install is of course the original drivers.

Thanks in advance.

---

### Post by taurus on 2006-11-22
Why not boot into recovery mode from GRUB menu and install or fix whatever there is a problem with your X.  And if you need to reconfigure your X again, just run

```
dpkg-recconfigure xserver-xorg
```

---

### Post by Bobtheknight on 2006-11-22
I'll try that except I don't think I get a grub menu.  All I see at boot-up is GRUB-loading 1...0... blank screen.

I'm not entirely sure what comes after GRUB because I have 1 second to stare  at it before it becomes 0 and turn off my screen.  Before the screen lights back up at login, except now it being broken, doesn't.

---

### Post by taurus on 2006-11-22
Okay, the next time when you get to the GRUB screen, hit the Esc key to bring up the menu.  Use your arrows key to move down to the second entry which is the recovery mode and hit Enter...

---

