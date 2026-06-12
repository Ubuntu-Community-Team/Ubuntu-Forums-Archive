---
title: "Don't Hide GRUB Menu on Bootup"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-24
Hi, I have managed to add Windows XP to the GRUB bootup menu. Currently, I have to press Escape within 2 seconds for the menu to come up. I want to be able to see the menu everytime I boot without pressing any keys. That way, I can choose each time I boot what I want to do. 
I am in the Grub menu.lst, and I see the option that says:
hiddenmenu

do I just add a # in front to get the menu to show or do I have to do something else?
Thanks for any help.

---

### Post by jken146 on 2008-03-24
Yes, just comment the line out with a #.

---

### Post by m60dude5 on 2008-03-24
That works. Thank you. Just wanted to make sure I wasn't messing anything up and wouldn't be able to boot.

---

### Post by Shazaam on 2008-03-24
More goodies=
1. Change this...
```
default		0
```
to whatever you want to boot first (starts at zero, count the kernel entries).
2. Change this....
```
timeout		5
```
to what you want (no less than 3).
3. Unmark this.......
```
#color cyan/blue white/blue
```
To change the colors of grub's boot screen (letters).
Lots of goodies there, think the changes through as you could goof it up. Back menu.lst up first. If you do goof up it is easy to fix with the livecd or in Recovery Mode.

---

