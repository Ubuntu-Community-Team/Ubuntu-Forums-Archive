---
title: "Envy Installation Help"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-24
So I used Envy for my nvidia geforce 7900.  When finished installing I restarted my computer and came up with an error screen saying something like your nvidia kernal drivers are not installed correctly.  
I had to restore the backup driver to get it to work again.
I was wondering, If im doing anything wrong in installing envy.
Please help.

---

### Post by martinw89 on 2007-03-24
This happened with me too, it was because I forgot to completely remove my previous NVIDIA drivers (the ones available through apt-get).

It sounds like you fixed it and are back in with old drivers, so run envy again.  But, select to remove NVIDIA drivers.  Then, install the new drivers again with envy.  Don't let envy configure Xorg, this also caused problems for me.  Instead, say no to configuring xorg, and run (in a terminal)
```
sudo nvidia-xconfig
```
Hope this works!
-Martin

---

### Post by zeroo on 2007-03-24
[QUOTE
```
sudo nvidia-xconfig
```
Quote]

So I just type this in terminal after installing envy and it should work?

---

### Post by martinw89 on 2007-03-25
Yup, hopefully!  However configuring X is unfortunately not the easiest or error-proof process out there and something still could go wrong.  But it it does go wrong, there's always these forums.

-Martin

---

