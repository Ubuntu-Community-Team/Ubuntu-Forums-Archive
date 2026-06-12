---
title: "No More Space in /"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by chrism66 on 2006-06-15
Hi all a real newbie question here. I installed steam into my home directory, then I installed Half-Life 2 (don't know where steam downloaded it to). So I tried to run Half-Life 2 and the computer actually froze I could not do anything but hit the reset button. Now when I try to log in I can't as my whole 10GB / directory is full. Any clues on what happen and how to remedy this? Thanks in advance for any help that can be provided.

Chris

---

### Post by nanotube on 2006-06-15
[QUOTE=chrism66]Hi all a real newbie question here. I installed steam into my home directory, then I installed Half-Life 2 (don't know where steam downloaded it to). So I tried to run Half-Life 2 and the computer actually froze I could not do anything but hit the reset button. Now when I try to log in I can't as my whole 10GB / directory is full. Any clues on what happen and how to remedy this? Thanks in advance for any help that can be provided.

Chris[/QUOTE]
boot from livecd, mount your / drive, and delete some crap from it. :) (find whatever stuff halflife put on it...)

---

### Post by taurus on 2006-06-15
May want to check the /tmp (or even /var/log).  Bet you have some large files in there, taking up all the space...

---

### Post by chrism66 on 2006-06-15
Hi all, Well I did some work and it seems that there was a directory in /media/cdrom0 that was 7GB in size that took up all that was left on my root drive. Deleted it and i am back up an running. Thanks all for your time and help!!

---

