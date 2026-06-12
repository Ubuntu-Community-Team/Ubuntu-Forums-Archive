---
title: "broke xorg now there is not even a login option"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-11-22
some how I screwed up big installing my nvidia driver. I broke x, witch is nothing new but now i just get a blinking cursor on a black screen after the red and blue error message comes up telling me x is broke. it doesn`t ask for my user name or anything and no commands work. any idea why it is doing this?

---

### Post by rlozano on 2006-11-22
> **onesojourner said:**
> some how I screwed up big installing my nvidia driver. I broke x, witch is nothing new but now i just get a blinking cursor on a black screen after the red and blue error message comes up telling me x is broke. it doesn`t ask for my user name or anything and no commands work. any idea why it is doing this?

try to boot from LiveCD and correct your xorg.conf. if there is a backup of your xorg.conf, i suggest that you revert back to that.

its in /etc/X11/xorg.conf.

btw, when you boot from liveCD, you may have to mount your primary partition.

hope this helps.

---

### Post by sunexplodes on 2006-11-22
Failing that, reboot and get into your GRUB menu, select recovery mode, and either edit xorg.conf from there, or enter dpkg-reconfigure xserver-xorg to rebuild it.

---

### Post by steve.horsley on 2006-11-22
It might be the "quiet" option in boot suppressing output on tty0. Try Ctrl-Alt-F2 and see if you are offered a login there.

---

