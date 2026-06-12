---
title: "no initial load screen"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Xiamen on 2008-03-03
I haven't seen another post with this problem so I'll post:

After the GRUB page, when I select Ubuntu to load, no load screen appears. The screen simply stays black but lit for 2 minutes, then the login page appears. Is this supposed to be happening or is there an error?

---

### Post by Superkoop on 2008-03-03
There are a few threads about this:
[http://ubuntuforums.org/showthread.php?t=579684](http://ubuntuforums.org/showthread.php?t=579684)
[http://ubuntuforums.org/showthread.php?t=579622&page=2](http://ubuntuforums.org/showthread.php?t=579622&page=2)
To name a couple. 

But I think the solution you are looking for is this:
Go to terminal and type the following:
```
 sudo gedit /boot/grub/menu.lst  
```

Scroll down to where it says:
```
# ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash
```
Or similar to that at least. And where it says "splash" change that to "nospalsh" (w/o quotes of course.)

that should get you booting much faster.

---

### Post by Xiamen on 2008-03-03
Thanks. That pretty much worked perfectly.

---

### Post by glennric on 2008-03-03
What Superkoop suggested won't really fix the problem.  That will make it so that there is no splash screen, and you will see all of the scrolling text.  To fix it so that you see the splash screen instead try 
```
sudo update-initramfs -u
```

---

