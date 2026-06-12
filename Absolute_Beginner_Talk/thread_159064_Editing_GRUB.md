---
title: "Editing GRUB"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-04-12
Hi All, 

I recently installed Ubuntu on my PC. and yes i'm currently running ubuntu! however i have two hard disks. a master and a slave. 20 gigs each. the ubuntu is running on the master with the GRUB loader. 

is there a way to edit GRUB so that i may install win 2000 on my  slave and have it also show in GRUB?

happy hunting.

---

### Post by dermotti on 2006-04-12
It would have been easier to install Windows first because then Ubuntu would have done everything for you. 

Your best bet know is to disconnect your Ubuntu drive and install Windows 2000, This way Windows 2000 wont write over grub. Then once its insallled, plug your ubuntu drive back in and add windows 2000 to your /boot/grub/menu.list

---

### Post by dermotti on 2006-04-12
oops double post

---

### Post by ProjectGod on 2006-04-12
never gave much thought to it... but when i disconnect the ubuntu drive. MASTER. don't  i need to set the other one as MASTER? if so after i install win2k on the other one which and reconnect the ubuntu drive... which one becomes master?

cheers

---

### Post by dermotti on 2006-04-12
You can temporarily make the windows drive master so you can install it. And once your done move it back to slave, then hook the ubuntu drive backup.

---

### Post by ProjectGod on 2006-04-12
excellent! thanks for that. :D

---

### Post by Mustard on 2006-04-12
The Grub entry for a windows install on a slave drive is going to be slightly different than the one for an install on a master.  Windows does not like being on the slave drive, so Grub tricks it into thinking its on the master. This entry below is what my menu.lst entry for grub looks like..

```
title           Windows 95/98/Me
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Note the two lines with 'map' entries on them.

---

### Post by ProjectGod on 2006-04-12
ahh ok. cheers.

---

