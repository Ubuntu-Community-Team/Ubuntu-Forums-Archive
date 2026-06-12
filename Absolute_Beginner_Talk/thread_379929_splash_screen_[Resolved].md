---
title: "splash screen [Resolved]"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dhaulk on 2007-03-09
Yea I just installed Ubuntu. I unplugged my primary drive and installed ubuntu on my slave then I made the required changes in the menu.lst so I could boot windows xp when I plugged my drive back in. Set my bios to boot from the slave. Everything works fine there I can boot either os. Now I downloaded a splash screen and copied it to the boot folder, It was labeled Ubuntusplash.xpm.gz . I added the entry

splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz

But when I reboot I get an error say it can't load the splash screen and to press any key to continue. Is there something wrong with that line or did I do something wrong?
Oh should it be (hd1,1) because Ubuntu is on the slave instead of the master drive?

---

### Post by yabbadabbadont on 2007-03-09
> **dhaulk said:**
> Oh should it be (hd1,1) because Ubuntu is on the slave instead of the master drive?

That is probably the correct answer.

---

### Post by aysiu on 2007-03-09
Grub splash images have very stringent requirements. 

Read more here:
[http://forums.fedoraforum.org/archive/index.php/t-1243.html](http://forums.fedoraforum.org/archive/index.php/t-1243.html)

---

### Post by dhaulk on 2007-03-09
OK well I changed it to (hd1,1) but it still don't work. Maybe I'll go back to the site I got it from and download another one.

---

### Post by yabbadabbadont on 2007-03-09
Like aysiu pointed out, make sure that you are downloading "grub splash" images.  They are quite different from other splash image types.

---

### Post by dhaulk on 2007-03-09
Ok I figured it out it was (hd0,0)

---

