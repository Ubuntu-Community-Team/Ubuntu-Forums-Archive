---
title: "DVD drive spindown"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-05-22
I have a DVD-Ram disk mounted in ubuntu that I use daily for backup purposes, however, lately the drive has not been spinning down and runs constantly.

I tried using hdparm to set the spindown time but the terminal returned "incorrect parameter".

Is there a reason why the drive keeps spinning and how can I set it to spindown after say 1 minute of idle.

the device is /dev/scd0.

---

### Post by Pragmatist on 2007-05-24
After examining these threads:
[http://www.linuxquestions.org/questions/showthread.php?t=250431](http://www.linuxquestions.org/questions/showthread.php?t=250431)
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

My guess is that you can control the problem by reducing your usage of swap (if you can live without it, as they mention)

---

