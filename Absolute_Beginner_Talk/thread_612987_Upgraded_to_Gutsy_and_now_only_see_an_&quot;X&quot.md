---
title: "Upgraded to Gutsy and now only see an &quot;X&quot;"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by glaze0101 on 2007-11-14
I upgraded to gutsy and all seemed to go fine but when I boot instead of getting a question about usr name and pwd I just see a image of an X

please help

---

### Post by celticbhoy on 2007-11-14
You say image, do you mean a mouse pointer or a larger image

---

### Post by glaze0101 on 2007-11-14
it looks graphical a bit larger than a mouse pointer.

I got to terminal and then typed in grub and then boot and it said that the kernel must be loaded before booting, which miught be the problem

---

### Post by celticbhoy on 2007-11-14
I use damn small linux on a very old laptop, and when the Xserver is starting it runs with an 'X' pointer for the mouse, I think this is what is happening to you. Dont know a solution, but if you boot into recovery and try 

dpgk-reconfigure xserver-xorg

it might help

---

### Post by glaze0101 on 2007-11-14
reconfigured xserver and now I still just get this X, you are right though it is the mouse (didnt even think of that before

---

### Post by glaze0101 on 2007-11-14
I re-ran upgrade and there ended up being a bunch of files that were not upgraded.  I got this error message though and still have the same problem of a black screen with an "X" which is my mouse:

errors were encountered while processing:
/var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

