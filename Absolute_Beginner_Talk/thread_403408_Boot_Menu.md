---
title: "Boot Menu"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-07
I recently installed Ubuntu after wiping my harddrive and making partitions (one for XP of course). I then installed XP, which of course stopped me from loading Ubuntu. I reinstalled the Grub loader and now I have no choice to get into XP. Can someone please   tell me how to edit the menu?

---

### Post by Biscuitpie on 2007-04-07
I REALLY need to know this. :(

---

### Post by confused57 on 2007-04-07
> **Biscuitpie said:**
> I REALLY need to know this. :(

Hi Biscuitpie,  I see you got Windows installed...here's how to edit  menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

then add your entry to boot Windows to the very bottom of  the file, something like this:

```
title       Windows  XP
rootnoverify   (hd0,0)
makeactive
chainloader  +1
```

quit & save

the above entry  should work if Windows is on your first partition

---

### Post by Biscuitpie on 2007-04-07
That worked, thanks!

---

### Post by Biscuitpie on 2007-04-07
One more question: When you first install Windows is there only going to be recycle bin on your desktop? I installed it kinda wacky and it's been a long time.

---

### Post by bobplano on 2007-04-07
well i think all the rest of the icons i had were trials so you're probably ok

---

### Post by brtnbrdr on 2007-04-07
Yes, that is normal.  You can add My Computer, My Documents, etc. by right-clicking on the desktop and selecting Properties, going to the Desktop tab, and clicking on Customize Desktop...

---

