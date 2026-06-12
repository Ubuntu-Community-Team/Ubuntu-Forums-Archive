---
title: "Refit still things I have linux installed but its not???"
date: 2007-07-10
forum: Apple Intel Users
---

### Post by erkker on 2007-07-10
I had a dual boot, with ubuntustudio using refti and everything worked but i needed my audio firewire interface to make it useful.  I deleted the partition using the bootcamp fix, but now refit still thinks that there is a linux boot option.  It doesnt really matter but I thought I would ask if anyone knew how it fix it?


Thanks

dont worry I used virtual box to get linux back on my machine.  It also allows me to audition multiple OSes

---

### Post by ronocdh on 2007-07-10
You should be able to edit the rEFIt script file in your root directory of OS X and remove (or at least comment out) any mention of operating systems you don't want to deal with. Have you confirmed in Disk Utility in OS X that the partition is not visible?

---

### Post by cyberdork33 on 2007-07-10
Linux is actually gone, the grub bootloader is just still in the MBR. You can overwrite it when you install windows (If that is the plan).

---

### Post by erkker on 2007-07-11
Which script in the root directory are you referring to because I do not see one.  There are several scripts in /efi/refit but when they are opened the options are not there.  The same goes for the refit.conf file: the only thing not commented out is the splash screen hold time.


Thanks


-E

---

