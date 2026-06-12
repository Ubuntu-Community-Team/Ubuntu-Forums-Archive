---
title: "Grub sees windows but wont boot"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by aceron on 2006-06-26
bit of a problem. I had ubuntu entirely on my laptop, then i just use my windows recovery cds to wipe it out (i had dapper running on my desktop). But windws would never boot, grub was still in the mbr. So i installed dapper via live cd on a seperate partition keeping windows on the hd. at first grub did not even see the xp drive, i fixed that but now when i try to load it from grub it flashes:
savedefault
makeactive
chainloader +1
then comes back to grub boot sreen (i can get into dapper just fine from this though)
my grub menu looks normal

so i'm really interested in a solution to this if anyone has had the same prob

also if in uninstalled grub from the mbr, would i then boot from windows?
if so then i could reinstall grub from there an it sould find xp since its reinstalling grub eh?
if i cant just fix grub (which is what I want to do) then i'll just make a win floppy an fxmbr and re install dapper, thanks

---

### Post by DCM36 on 2006-06-26
I'm guessing you also have this "root   hd(x,y)" above those three lines, x referring to the hard drive, which is probably 0 because its a laptop, and y referring to the partition windows is installed on. If you aren't sure which partition is windows, you can make a few enteries in menu.lst starting with hd(0,0) hd(0,1) and so on. Post back if it still doesn't work.

But if this isn't your problem, then im out of ideas.

---

### Post by aceron on 2006-06-26
yeah its 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1
 
i did change it to (hd0,1) but there was no change
here is this info

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1307    10498446    7  HPFS/NTFS
/dev/hda2            1436        2200     6144862+  83  Linux
/dev/hda3            1308        1435     1028160   82  Linux swap / Solaris

---

### Post by DCM36 on 2006-06-26
im stumped then, im guessing your best bet would be the win floppy to get windows back.

---

### Post by Apple 101 on 2006-06-26
The makeactive line should not be in your menu.lst file for Windows if it was automatically added by the Debian installer.

---

