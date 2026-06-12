---
title: "Solution for LCD backlight controls on Macbook Pro 5,5 12.04 Precise Pangolin"
date: 2012-08-15
forum: Apple Hardware Users
---

### Post by michaeldmills on 2012-08-15
Greetings!  I recently moved to Ubuntu 12.04 on my 13" Macbook Pro 5,5 from Lion and couldn't be happier.  I had a few years of flirtation with OSX but have come back home to the roost.
 
Out of the box everything seems to work without the need for the pommed install (though that is mentioned as a to-do on the wiki for the install).  The only thing I had problems with is the LCD brightness keys not working.
 
After a fair amount of searching and trying a few things, I found an easy solution.  
 
[https://github.com/guillaumezin/nvidiabl](https://github.com/guillaumezin/nvidiabl)
 
There is a kernel module that can be installed and loaded up and it works great.  Just be sure to add **nvidiabl** to your /etc/modules file to load on boot.  
 
I hope this isn't a double post on the forums, but if so, rookie mistake :-)

---

### Post by cephinux on 2012-09-06
Thanks worked for me, although I think I can't go to the maximum brightness level any more. Correct me if I'm wrong.

---

### Post by zaebo on 2012-12-18
You are right. It is the same for me.

Working brightness control vs. maximum brightness...

..puh.

---

