---
title: "Changing Grub boot priority?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-02-01
How do I change the boot priority in Grub? 
Ubuntu is messing around on a friend's computer and I want it to boot into XP at countdown until I have had a go at fixing all the Ubuntu bugs.

---

### Post by jan quark on 2008-02-01
run in terminal

```
sudo gedit /boot/grub/menu.lst
```

and set the default to 1

the 1 means select second entry  as default

---

### Post by jan quark on 2008-02-01
you have to select the number which is the entry of the windows loader

---

### Post by jan quark on 2008-02-01
kernel = 0, 1 recovery mode = 1, 1 mem test = 2, 1 other operating system title = 3 and 1 other operating system = 4.

---

### Post by spiderbatdad on 2008-02-02
the correct way to do this is to put the windows partition first in the list of boot options, not to change the default number. The simple reason is that if a kernel upgrade adds itself to the list, the number would be wrong.

---

### Post by Roger Mudd on 2008-02-02
> **spiderbatdad said:**
> the correct way to do this is to put the windows partition first in the list of boot options, not to change the default number. The simple reason is that if a kernel upgrade adds itself to the list, the number would be wrong.

I used to do this when I dual-booted, however, any kernel upgrade would wipe Windows from the GRUB list completely when positioned as the primary boot OS. I'm not sure of a solution, but I do know it was a hassle ;-)

---

### Post by MarkX on 2008-02-02
Thanks everyone, will do as said!

---

### Post by MarkX on 2008-02-02
> **spiderbatdad said:**
> the correct way to do this is to put the windows partition first in the list of boot options, not to change the default number. The simple reason is that if a kernel upgrade adds itself to the list, the number would be wrong.

So how's that done then? Would be nice to have a GUI way of doing it from System/preferences...!

---

### Post by spiderbatdad on 2008-02-02
you would open /boot/grub/menu.lst with sudo privileges. ```
gksu gedit /boot/grub/menu.lst
``` scroll down to find the block of text containing the windows partition...probably near the bottom, under Other Operating Systems. Copy the entire four or five lines in the block by dragging your mouse over the text and right clicking and selecting copy. Then scroll up to ####END DEFAULT OPTIONS#### (something like that...where the Linux kernels begins. Be at the end of the above line and hit enter to insert a paragraph/line, then right click and select paste. 
Copying is better than cutting in case you have the problem of a kernel upgrade overwriting your entry. If that happened, you would have to repeat the above procedure.

---

### Post by spiderbatdad on 2008-02-02
ah there is a gui...I believe it is called startup manager...I will try to find it. Good Call! I think it can be found at GetDeb.com

---

### Post by spiderbatdad on 2008-02-02
[http://www.getdeb.net/search.php?keywords=startup+manager](http://www.getdeb.net/search.php?keywords=startup+manager)

NOTE: USE AT YOUR OWN RISK. THIS PROGRAM COULD MAKE YOUR SYSTEM UNABLE TO START.

---

### Post by MarkX on 2008-02-02
> **spiderbatdad said:**
> [http://www.getdeb.net/search.php?keywords=startup+manager](http://www.getdeb.net/search.php?keywords=startup+manager)

NOTE: USE AT YOUR OWN RISK. THIS PROGRAM COULD MAKE YOUR SYSTEM UNABLE TO START.

Hmmm.... Scared to install that but a 100% working version of this should be part of the install in future releases. Any new user would feel better knowing he can change the default in a few clicks instead of having to trawl forums and then ask for help.
Thanks for pointing it out though!

---

