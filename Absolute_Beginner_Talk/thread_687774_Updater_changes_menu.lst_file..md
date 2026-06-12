---
title: "Updater changes menu.lst file."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by powerpleb on 2008-02-04
I have a dual boot system with Ubuntu 7.10 and XP. Ubuntu is on the 1st hard disk and XP the second, this is not out of choice but the result of my BIOS as the 1st drive is IDE and the second SATA2. 
So my problem is that whenever there is an update that affects GRUB, the default seems to be to assume that XP is on the first drive and change the configuration accordingly so I get error 17 in GRUB. I have to go in and manually edit the menu.lst file and relate all of the Ubuntu boot options back to the correct drive/partition.
Is there a way to stop this happening? It's not a very serious issue, it's just that moment when my heart skips a beat every time my system won't boot.

---

### Post by Blutack on 2008-02-04
You may have put the XP stuff in the "Automagical" section - this is the bit that gets changed.  It needs to go after like this:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP
root            (hd0,2)
chainloader +1


---

### Post by Blutack on 2008-02-04
You can check it's worked by running
> sudo update-grub
and checking the file is the same.

---

### Post by powerpleb on 2008-02-04
> **Blutack said:**
> You may have put the XP stuff in the "Automagical" section - this is the bit that gets changed.  It needs to go after like this:

Thanks for the superfast reply!
I checked and it seems to be already there. I'll post the contents of that part of the file anyway.
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


I've just seen a line that may be relevant. 
> ## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false
If I unhash lockold=true would that do it?

---

### Post by Blutack on 2008-02-04
No, that refers to passwording old entries.  Odd one you've got here...
Can you delete everything under 
### END DEBIAN AUTOMAGIC KERNELS LIST
and add in something simple like this
> title Windows XP
root (hd0,2)
chainloader +1
Ensuring that you adjust root for the correct drive (hd1,0) maybe?
Then run update-grub and see if it gets monkey'd with...

---

### Post by powerpleb on 2008-02-04
Thanks a lot for that.
I changed groot=(hd0,0) to groot=(hd1,0) and it worked.

---

### Post by Blutack on 2008-02-04
Does your XP work is the real question...
:)

---

### Post by gkestrel on 2008-02-05
I have experienced similar problems myself when using both sata drives and ide drives. I usually fix the grub issue first by booting with a super grub disk and letting that fix grub, but then found that every time the kernel updated i had the grub problem return. After searching on the net i found that occasionally Ubuntu gets the device map for the hard drives wrong and has taken a best guess during the install. I was able to fix this by doing the following

before starting make sure to backup of /boot/grub/menu.lst and /boot/grub/device.map
To fix your /boot/grub/device.map type sudo gedit /boot/grub/device.map and change it
mine original was like this

(hd0) /dev/sda
(hd1) /dev/sdb

i then changed it to

(hd0) /dev/sdb
(hd1) /dev/sda

then save the file

I then renamed /boot/grub/menu.lst to /boot/grub/menu.lst.old
then updated grub by sudo update-grub

As a precaution do sudo gedit /boot/grub/menu.lst again and check to see if it contains the correct entries for your windows installation mine did not, so i had to copy the correct entry from the old version of menu.lst so as to be able to boot into windows correctly.
Also if you have any splashscreen enabled you will need to add again the line to enable it.

---

