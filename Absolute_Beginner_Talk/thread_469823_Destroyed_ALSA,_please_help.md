---
title: "Destroyed ALSA, please help"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by stealth_monkey on 2007-06-10
Well, I've done my first major screwup in linux yet. Plus side I have a backup, downside is that I don't know how to use it. Yes, I'm a horrendous noob. I followed the instructions in post 8 of this thread [http://ubuntuforums.org/showthread.php?t=382645](http://ubuntuforums.org/showthread.php?t=382645) to the letter, and I now no longer have the ability to play sound. Would anyone be kind enough to tell me how to use the backup I made in the first step?

---

### Post by stealth_monkey on 2007-06-10
Nevermind, I figured it out for myself. Just on the off chance someone out there has made the same mistake I have, here's how to restore the backup.

1) Extract the backup archive anywhere convenient
2) press alt+f2, run "gksu nautilus" (without the quotes)
3) Copy the extracted folder, go to file system (wherever you find the lib folder)
4) Paste, select replace all
5) Open a terminal and enter:
sudo depmod -a
then
sudo dmesg -c >/dev/null

reboot and pray

---

