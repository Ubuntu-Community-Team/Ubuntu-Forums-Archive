---
title: "How can u rename dual boot?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Lancelot on 2005-11-15
Hello guys, am absolute beginner..

I want to rename this dual menu...

Ubuntu, kernel 2.6.10-5-386
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
Ubuntu, kernel memtest86+
Other operating systems:
Microsoft Windows XP Professional     -----------> i want to rename this as blank or
                                                                              what ever..

Pls help me..and another...i want to hide the partition of Xp 

thanks..

---

### Post by andrewsawyer on 2005-11-15
Hey,

You need to do the following (and I'm assuming you're using Ubuntu not Kubuntu)
```
sudo gedit /boot/grub/menu.lst
```
If you are using Kubuntu, then just replace gedit with whatever the KDE equivalent is.

Then scroll right down to the bottom.  You should see the section that relates to Windows.  It will be 4-5 lines, starting 'title' and ending 'boot'.  Just put a # infront of each of the lines relating to Windows.  Save the file, and that should be it.

To get it back, just follow the same steps and delete out the #'s that you just put in.

Hope that helps.

---

### Post by Lancelot on 2005-11-15
hey! thanks a lot!

Thanks for the help..

---

### Post by andrewsawyer on 2005-11-15
No worries - it's about time I helped out in these forums!

---

