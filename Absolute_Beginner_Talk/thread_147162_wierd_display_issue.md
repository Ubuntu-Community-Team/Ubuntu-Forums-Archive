---
title: "wierd display issue"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by EllieB on 2006-03-19
I'm really new at linux, so I'm using the Ubuntu Live CD (I'd hoped to install it), and it loads just fine until I get to the desktop, when the display has these fuzzy vertical lines about an inch apart...  The computer works fine when I boot Windows XP.  And when I tried the Knoppix boot CD, the display was even worse: completely unusable, since the whole screen was fuzzy.  I've tried booting with different resolutions, but nothing helps- any suggestions?
Any help is MUCH appreciated!

P.S.  It's an older computer (2000)-- Gateway, pentium 3

---

### Post by taurus on 2006-03-19
Sounds like X uses a wrong vertical & horizontal refreshing rates for your monitor then!!!

---

### Post by trent dillman on 2006-03-21
Try Knoppix again, when it gets funky looking, press CTRL+ALT+F2

This should show something like

root@knoppix:~#

then post the output of these commands:

lspci | grep VGA        <----that's a pipe in the middle, not an ' L ' or an ' i '
grep -e Driver /etc/X11/xorg.conf

and pray you don't see neomagic (j/k) :-P

---

