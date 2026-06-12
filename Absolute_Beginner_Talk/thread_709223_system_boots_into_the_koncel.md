---
title: "system boots into the koncel"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by twooknee1 on 2008-02-27
Hi everyone I have just recently come into position of umbutu from a friend I installed it and it was working great but then I started to experiment I opened a konsul window and I also opened a root koncul window it asked for the password to which I gave it things seemed ok, so I left not knowing what to do, anyway I went to set the time and pressed the admin button and put my passwd in, and to my surprise it said, sorry but "su failed!" I have no idea what that meant, anyway I restarted the computer again and know it wont boot further than the konsul, with the cursor looking something like this (twooknee1@umbutu $_) and no matter what I do I cant get into the desktop, although it seems everything is loaded, as when I dir it replies Desktop, please can some one help me, I been trying all night, I would be so great full, if some one could point me in the right direction. Thank you..

---

### Post by Cypher on 2008-02-27
Attempting to set the time and failing to do so shouldn't necessary cause any harm, least of all not allowing you to boot up completely. In the GRUB menu are you choosing the default Ubuntu option or the one with the words (recovery console) on it? If the second one, then it's supposed to drop you to the console for you to fix anything that's broken. If you're choosing the first option and still being dropped to the console, then try
```

sudo dpkg-reconfigure -phigh xorg-server

```
and go through the steps, then reboot and see what happens

If that doesn't work and you're back to the console on the reboot, then try
```

startx

```
and see if the desktop shows up..

PS, It's Ubuntu and console, not "umbutu" and "konsul"..;)

---

### Post by djbsteart1 on 2008-02-27
```
sudo startx
```

this will start the xserver and give a graphical environment.
you may get warning messages about things not starting. if so, log out, then restart.

if you get a warning about being root user, then log out and log back in as yourself.

that should be you back on the road.

---

