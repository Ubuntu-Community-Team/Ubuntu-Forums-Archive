---
title: "want to add some time to grub application screen"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-04
I realize you have 3 seconds to hit the ESC button on a dual boot.  I just want to add a few more seconds just so I can find it(bifocals suck).  How do I do it.  I saw a thread on it last week.  Couldn't find it again.  Just want to know where to go and how to add some time.  Thanks.

Mark Shuman

---

### Post by tamoneya on 2008-04-04
```
sudo nano /boot/grub/menu.lst
```
search for "timeout 3" and change it to your liking

---

### Post by kerry_s on 2008-04-04
press alt+f2
type> gksudo gedit /boot/grub/menu.lst

change
timeout		3
to what ever you want

---

### Post by ubuntu-freak on 2008-04-04
You can also install startupmanager. Launch it by navigating to System>Administration>Start-Up Manager. It lets you easily change boot options, including which OS to boot by default.
 
Nathan

---

### Post by munkyeetr on 2008-04-04
You can also just hit one of the arrow keys at the boot screen and the time-out stops counting...

---

