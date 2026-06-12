---
title: "dual booting help."
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Dark Charizy on 2006-07-30
How do I dual boot. I have install ubunto 6.06 on my d drive that is a ide drive (FAT32)and my windows xp home sp2 is on c drive that is a sata drive (NTFS) but the ubunto didn't pick up the windows os while installing. I used the livecd to intstall.

---

### Post by john 44 on 2006-07-30
I assume Ubuntu is booting ok when your BIOS is set to boot that ide disk first? 

To boot Windows from Ubuntu/grub, you need to edit your /boot/grub/menu.lst file like so to boot windows on the sata disk:

title Windows 
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

Either add that entry or edit the existing entry for Windows. The menu.lst file is simply a text file that can be edited like any other text file.

Windows expects to be set to boot 1st from the BIOS. What the map command does is cause grub to boot windows as though it is indeed first in your BIOS.

You can also boot windows by changing your BIOS to boot to that sata hard disk first, but that is annoying.

---

