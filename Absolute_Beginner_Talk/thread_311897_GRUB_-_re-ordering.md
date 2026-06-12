---
title: "GRUB - re-ordering"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by mnduck on 2006-12-03
Finally got UBUNTU running but would like to have W2k as the default in grub.

How do I achieve that please? Some Doc I need to read?


Many Thanks           mnduck

---

### Post by taurus on 2006-12-03
You need to edit /boot/grub/menu.lst and change the "default" from "0" (for first entry) to whatever your Windows is, usually the fourth entry which means the number should be 3... 

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by atoponce on 2006-12-03
There are a couple ways to do this.  You can either cut and paste the Windows section of /boot/grub/menu.lst above the Ubuntu listings, or you can set the nth listing in the file as the default.  Not near an GRUB listing at the moment, but it seems to me there was an option "savedefault" or something like that, where you set the listing as a default with a number.  So if Windows is the 4th listing in the listing, savedefault=4.  There is documentation in the file though, that will help you.

---

