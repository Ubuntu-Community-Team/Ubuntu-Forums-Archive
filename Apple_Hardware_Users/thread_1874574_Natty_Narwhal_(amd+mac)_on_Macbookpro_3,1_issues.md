---
title: "Natty Narwhal (amd+mac) on Macbookpro 3,1 issues"
date: 2011-11-03
forum: Apple Hardware Users
---

### Post by HotForLinux on 2011-11-03
- GRUB -
g1) After installation on a separate partition (dual boot), Grub set up a menu list woth two entries for booting MacOS: for 32 and for 64-bit kernels. Is that the way it should be?. I don' think both kernels are installed? Moreover, none of them boots the MacOS. One, the one I think it should work, gives an immediate error because ir doesn't find the kernel,  and the other starts booting and stops in the middle of the booting process.

g2) If I select quiet spalsh in grubs boot command, a horrible screen is shown.


- CONSOLE -
c1) The console fonts are ridiculously big, so I changed the font to be:
FONTFACE="Terminus"
FONTSIZE="12x6"

 in /etc/default/console-setup  

After that, I ran the command:
$sudo setupcon

Is that the correct way to do it? (the information is really bad)
Now it looks better but it is still too big and often, like when I boot to recovery mode, this font is not used.

---

### Post by HotForLinux on 2011-11-06
-- bump --

---

