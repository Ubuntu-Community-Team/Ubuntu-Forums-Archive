---
title: "Grub shows me two recovery choices"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-02-10
Bunches of questions about the 2.6.17-11-generic update of this morning.

As near as I can tell, 2.6.17-11-generic is running ok. I lost my wireless driver but got it back and all is well there.

I now have both 2.6.17-10-generic AND 2.6.17-11-generic on my computer. I am defaulting to the new kernel.

GRUB is presently showing 2 "recovery "  choices. One is referring to 2.6.17-11-generic. The other recovery choice is for 2.6.17-10-generic. 

So if I am up and running and everything seems ok, why am I being offered these recovery choices  by GRUB and what do you do about them? 
Should I keep doing the recovery choices until they go away or what.? Is there a way to verify the system?

Jim

SOLVED --

---

### Post by neilp85 on 2007-02-10
When you update to a newer kernel version it adds both the normal and recovery boot options to /boot/grub/menu.lst. Everything else is left untouched so the older options are still there. If you don't want grub to show those options comment them out of your menu.lst file.

---

### Post by Jim Rogers on 2007-02-10
Thank you very much. I guess I will leave them for a bit, just to be safe, then I will find menu.lst and   comment the out.

Jim

---

