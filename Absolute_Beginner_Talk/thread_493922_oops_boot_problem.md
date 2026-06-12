---
title: "oops boot problem"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by dnathe4th on 2007-07-06
So i thought i'd be slick and add some stuff in a script and run it on boot.  unfortunately i mseed up somewhere and cannot boot at all.
After the UBUNTU screen with the orange bar, the screen goes black and the computer shows no read-write ops, just that its still on.

how can i boot ubuntu to remove my update-rc.d mistake?   or do i have to reinstall.

---

### Post by Cypher on 2007-07-06
First thing to try is to choose the Recovery option in the GRUB Menu. If you don't see the menu, hit ESC when the PC boots up. In recovery mode you should be able to delete whatever you added.

If that doesn't work for you, then you can use the LIVE CD to boot into Ubuntu and then mount your hard drive and make the changes..

---

### Post by dnathe4th on 2007-07-06
OK
the GRUB menu worked, i deleted what I had, and booted up find
but the enxt time i booted, and every subsequent time now, it tells me GRUB is missing hte file menu.1st or something.
Pretty bad by the looks of it

---

### Post by twiceasworn on 2007-07-06
Could you post the exact error you are getting?  If all you did was remove the script that you created, GRUB shouldn't be yelling at you.

---

### Post by Cypher on 2007-07-06
..and what exactly did you erase???

---

### Post by dnathe4th on 2007-07-06
```

#!/bin/bash

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

not too bright, prolly not even what i should have run.  but that was what i put and what i erased.
i'll post back wither hte current error i get when i try to boot

---

### Post by dnathe4th on 2007-07-06
boot error as follows:
```

Booting 'find /wubi/boot/grub/menu.1st'
find --set-root --ignore-floppies /wubi/boot/grub/menu.1st

Error 17: File not found

Booting 'find /menu.1st'
find --set-root --ignore-floppies /menu.1st

Error 17: File not found

Press any key to continue
```

---

### Post by dnathe4th on 2007-07-08
SHould I just reinstall everything?  I see no other way of giving any commands

---

