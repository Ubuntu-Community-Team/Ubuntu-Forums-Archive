---
title: "Very slow loading into Desktop!"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2007-02-19
Hello. Recently when I type my password and log into the system, the ubuntu gnome splash screen takes very long to appear, and the desktop contents take quite long to appear after that. How can i figure out the cause of the sluggishness? Thanks!

---

### Post by lhtown on 2007-02-19
This might seem like a dumb question, but do you have a very large image set as the background for your desktop or are you autoloading prgrams with QT/KDE dependencies?

---

### Post by tronica on 2007-02-19
just a thought, if you don't have much memory, ubuntu could be using the swap.

---

### Post by nyxynyx on 2007-02-19
Thanks for the replies!

I removed my wallpaper and loading times weren't affected. I'm autoloading beryl, kiba-dock, gaim. I have 2GB of memory. And I don't have a swap file.

This slow down only started recently.

---

### Post by nyxynyx on 2007-02-19
I did quite a bit of restarting. Sometimes the delay is only 4 sec. I rebooted immediately and the next time i load into desktop the delay is 20sec. Puzzling!

---

### Post by lhtown on 2007-02-20
I don't have any good ideas for this problem. If you care to tell us more about your system and setup, maybe it would trigger something.

---

### Post by nyxynyx on 2007-02-22
I have a laptop: Core2Duo, 2GB DDR2, 80GB HDD with >50% free space, Geforce 7400Go. Running Ubuntu Edgy. Im using beryl, a dark GTK theme. Restarting x is very fast. Starting from cold takes quite long, around 20-30sec compared to the fast 3-5sec for my desktop to appear when ctrl+alt+backspacing. I've done some tweaks ([http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)) and disabled some services  following a Howto from Ubuntuforums. I think it boots faster if i idle at the gdm login screen for awhile, but i'll have to try this again.

Any suggestions?

---

### Post by lhtown on 2007-02-22
If your root partition on your hard drive were full even though you have tons of space on other partitions, it might cause a similar problem.

I really don't have any other good ideas except for looking in the log files.

---

### Post by nyxynyx on 2007-02-22
Hi! My root partition is 75% free. Which log files should i check, and what shd i check for?

Waiting awhile at the login screen does make the desktop appear/load faster.

---

