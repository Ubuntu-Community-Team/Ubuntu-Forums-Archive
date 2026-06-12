---
title: "Monitor going to sleep on boot up"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by darkadvice on 2007-08-20
Fiesty problem ~While trying to configure my xorg.conf, i didn't do the press enter till done, and looked at the options to improve perfomance,, so down the line i switched depth from 24-16... and then when i restarted computer welll Monitor Goes to sleep before the splash screen loads. And I have no idea how to fix a problem when i can't see a thing.

Right now i'm runnig off a live CD from dapper days, so does anyone know how to fix this?

---

### Post by ddrichardson on 2007-08-21
Try CTRL-ALT-Backspace - if it kills the Xserver - bringing the monitor out of sleep. Chances are its a bad mode.

To rectify, CTRL-ALT-F2 to a new terminal and log in, reconfigure X and away you go.

---

