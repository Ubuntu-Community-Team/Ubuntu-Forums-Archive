---
title: "[SOLVED] cant boot ubuntu/windows after installing 8.10"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by captainkz on 2008-12-04
Tried installing ubuntu today, had a host of problems, here's what I did step by step and the resulting problems.

downloaded and setup refit
disk utility wasn't working to repartition, so used gparted off ubuntu cd to repartition my OS X partition, leaving ubuntu about 30 gigs to install to.

Formatted empty 30 gigs as ext3 and installed ubuntu onto it.
rebooted, windows no longer in refit list
attempted to boot ubuntu, got a black screen with a flashing _. 

synced partition tables with refit as suggested in FAQ, now it just hangs at the picture of tux when i try and boot ubuntu from refit

Still unable to boot windows, windows partition labelled as disk0s3 in disk utility, verify and repair both unsuccessful, can't even access files.

os x still boots fine.

any suggestions to get windows and ubuntu working?

its windows vista ultimate and a 2007 aluminum imac if that helps.

---

### Post by utsuprainfra on 2008-12-04
is refit a boot manager like lilo or grub?

---

### Post by utsuprainfra on 2008-12-04
i think you need to install grub onto your linux partition.

---

### Post by captainkz on 2008-12-04
Installed grub with a livecd, ubuntu boots up fine now, and I can see my vista install in the grub menu, but when I select it the screen flashes for a second then goes back to the grub menu, any more ideas?

---

### Post by falcon61102 on 2008-12-04
Could you post the contents of your menu.lst, specifically the end portion that lists all of OS's that can load.  You can get to it by:

```
gksudo gedit /boot/grub/menu.lst
```

Then just copy the bottom portion here.

---

### Post by captainkz on 2008-12-04
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7506b095-6a61-462a-8cd6-a439376debc2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7506b095-6a61-462a-8cd6-a439376debc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7506b095-6a61-462a-8cd6-a439376debc2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7506b095-6a61-462a-8cd6-a439376debc2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7506b095-6a61-462a-8cd6-a439376debc2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1
```

edit: just guessing, but will adding makeactive after savedefault fix it? been a while since i've had to mess with grub
edit again: guess not, did nothing :/

---

### Post by falcon61102 on 2008-12-04
Based on how the GRUB just loops back to the menu when you select Windows, I wondering if you didn't overwrite the Windows boot section sometime with all that moving around that you did.  To fix this, I think you'll need to restore the Windows boot loader with a windows cd, then re-install the GRUB again.  There may be a quicker way that I'm unaware of, but that should fix it.

Another option is to check out the Super Grub Disk and use it to repair things.  [www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by captainkz on 2008-12-04
got it working, had to repair winload.exe after i got windows booting again, which then broke grub, so i reinstalled grub again.

mini guide to fix this issue

Fixing ubuntu boot:
boot a livecd, install grub
this will make ubuntu bootable again, there may be specific steps needed, see grub install guides for help there

boot vista cd, run repair, open command prompt, do bootrec /FixMbr
this should make vista bootable
you may get an error about winload.exe being corrupted, boot off the windows cd and go to repair again, use the automated repair and this will restore any corrupt files

you'll probably have to install grub again, just do it same as before.

you should now have a working triple boot system  :D

thanks to everyone who helped me out with this.

---

### Post by falcon61102 on 2008-12-04
Glad you got it fixed.

---

