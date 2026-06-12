---
title: "Completely reinstall x"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Kirky_D on 2006-09-26
after messsing up with xgl and compiz, i decided to go back to xorg.

Only problem being. that i appeared to have broken X while in the process.

is there any way to totally reinstall X?

Cheers gang!

---

### Post by whizbaby on 2006-09-26
Have you tried
**sudo dpkg -reconfigure xserver-xorg**
?

---

### Post by Kirky_D on 2006-09-27
Yes I tried that several times in recovery mode, then used startx which didn't work, but i Just tried it again now and rebooted into normal mode and it works fine, there must be no X server in recovery, which i did not know. lol

Cheers for the help

---

### Post by whizbaby on 2006-09-27
> **Kirky_D said:**
>  there must be no X server in recovery
So that you can work around problems with X...

---

