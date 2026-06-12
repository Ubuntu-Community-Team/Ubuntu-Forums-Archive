---
title: "Gutsy is making my gut churn--all is broken!  What to do?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-10-22
My "Update Manager" suggested I update to Gutsy.  Dutifully I did, not realizing I should have gone on the internet and searched for the disclaimer that says "Don't touch new distributions until three months after their release".  Now my computer is seriously messed up.  My nvidia driver doesn't work and the restricted drivers application won't download the necessary packages.  It boots crazy--flashing on-and-off text screens before flashing black, then more flashing screens, then finally settling into the normal logon.  Things are working weird.  What do I do?  If I do need to reinstall, how do I do it and how do I back up all my installed programs and settings?

---

### Post by ezak on 2007-10-22
Try running:

sudo dpkg-reconfigure --all 

A complete reinstall is not needed most of the time. Although sometimes it is indeed faster than manually fixing by process of elimination. ;-)

---

### Post by Bakon Jarser on 2007-10-22
Try Envy for fixing your video driver.  Ubuntu does recommend a clean install instead of upgrading.  You would download a live cd from the main website or from a torrent.  As for backing up your settings and programs, I'm not really sure.  I'm sure that many of your programs have settings files that you can back up.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  [envy's website]

**Edit:** Be sure to read envy's faq before using it.

---

### Post by gubemton on 2007-10-22
Argh, I ran that command that is reconfiguring my package and I have no idea how to answer these prompts.  It's halfway through already.  What now?

---

### Post by LanDan on 2007-10-22
well either you continue or you cancel ;)

---

### Post by Caffeine_Junky on 2007-10-22
....for best results (or chances there of) I would suggest a fresh install of Gutsy, or any OS for that matter.

Best of luck in what ever you choose to do...

---

### Post by Tony3286 on 2007-10-22
[SIZE="2"]  If a fresh install is done AND I have previously backed up my  /home directory - can I copy that
backup to the new Gutsy /home to have all my previous programs and preferences back?
If so, what would be the best way to do that? [/SIZE]

---

