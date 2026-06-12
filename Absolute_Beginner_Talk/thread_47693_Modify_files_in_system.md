---
title: "Modify files in system"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by noid1037 on 2005-07-09
I have an idea I need to add some info to some files to adjust the resolution but I havent figured out how to write info to the files.  What program/writer-reader should I use to open the file up and add info to save for the next time?

I can open up the files thru files management section but cannot mod... when I use Evolution- it is in ready only... please advise.

---

### Post by hamiltonlight on 2005-07-09
Hello. 

The way I open the files up is to enter the following in a terminal...

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

This way you have a backup of the file in case anything goes wrong. I learnt the first time!! 

Good luck.

---

