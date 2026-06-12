---
title: "Primary Boot Device"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by kapellen421 on 2006-12-06
I want my system to by default boot off of Windows instead of Ubuntu, How do i go about doing than?

---

### Post by davmac on 2006-12-07
Open up a terminal and type "sudo gedit /boot/grub/menu.lst"

Near the top of this file you'll see something like "default 0". Change this value to match the corresponding item for Windows. On my system it is 4. Save the file and next time you restart it should work as you want.

If you can't remeember the order of the items on the grub menu, just look towards the bottom of the menu.lst file and you'll see them all there, and remember it starts at 0 and the "other operating systems" line also counts as an entry.

Hope this helps,

Dave Mac

---

### Post by kapellen421 on 2006-12-08
Thanks Dave.  :cool:

---

### Post by tashe on 2008-01-14
But then how do you choose to boot Ubuntu at the startup?
I want to do the same thing

---

### Post by dstew on 2008-01-14
Editing the default value only affects which OS will boot if you do nothing and the time expires, or if you just press Enter. You can select any of the other OS's with the up/down arrows. As soon as you hit the arrow key the timer stops, and you can select another OS at leisure.

---

