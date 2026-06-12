---
title: "Too high resolution?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ithuwakaga on 2008-01-26
This is probably a pretty easy problem to fix, but how to I get Ubuntu to stay at 1024x768@60hz while it's booting?  I can see GRUB, then it changes resolution too high when I boot into Ubuntu, and then the login screen goes back to 1024x768.

It's not a major issue, but it's a very present annoyance.  Any ideas?

---

### Post by erginemr on 2008-01-26
Hi,

This is a classical usplash resolution issue that many people suffer from, emerged as a bug unfortunately with the release of Gutsy. To resolve it, refer to the last page of:
[http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216)

---

### Post by h0ax on 2008-01-26
I had this same issue.

I just changed my grub boot, and removed the 'splash' option.

sudo gedit /boot/grub/menu.lst
then scroll down and find the one that you usually boot to, then where it says 'splash' at the end, delete that, then when I reboot I don't see the "pretty" Ubuntu scrolling splash, but I see my beautiful command line-esque boot process ^_^

---

