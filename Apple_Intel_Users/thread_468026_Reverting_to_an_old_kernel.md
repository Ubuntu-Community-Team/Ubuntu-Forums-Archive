---
title: "Reverting to an old kernel??"
date: 2007-06-08
forum: Apple Intel Users
---

### Post by erkker on 2007-06-08
Hello all,

I did a dumb thing.  I managed to get my wifi working on my new MBP C2D,on ubuntu studio with the low latency kernel.  The only problem is that I did that before updating my system for the first time and when Ubuntu upgraded my kernel then I lost my madwifi.  Something is wrong with my keyboard layout so I cannot get into my grub menu to boot the old kernel because it wont register the escape key.  How do I revert to my previous kernel from the terminal.  I bet I can get it working with the new kernel but i dont have consistent access to a land line and I need to get the wireless working so iIcan download the new headers for my kernel and rebuild madwifi.


thanks

-E

(from inside OSX)

---

### Post by Jussi Kukkonen on 2007-06-08
Edit menu.lst, find the variable "default" and change the number to the number of the kernel you want to boot. See the list in the end of the file to find out what number you should use: the first kernel listed is number zero, then next one is number one and so on.

---

### Post by alloydwhitlock on 2007-06-08
Yeah, the darn escape key doesn't work to get into the GRUB menu.  It's pretty annoying, but there is a way around it.

Go into the terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

From there, follow Jussi's instructions on changing the default kernel.  


If you still have issues, just check out this web site:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

