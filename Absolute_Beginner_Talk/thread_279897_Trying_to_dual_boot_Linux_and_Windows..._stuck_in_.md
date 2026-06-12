---
title: "Trying to dual boot Linux and Windows... stuck in Linux"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by GuiltySpark00 on 2006-10-18
](*,) 

Hi everybody!

So here's the scoop:
After moving my Windows OS from my small drive (15 gig) to my large drive (80 gig), I was half goaded into installing XUBUNTU onto the small drive.  I had a Windows OS present on the 80 gig drive at time and, in order to install XUBUNTU, I had the XUBUNTU installer wipe my 15 gig drive and install itself afterwards.  So after all of that wrapped up and I restarted my computer and I wasn't allowed to boot Windows, no matter what I tried (boot priorities, stuff like that...).

Why can't I boot Windows?

---

### Post by bulldog on 2006-10-18
If you have a windows disk try in recovery console fixboot.

But can you tell me which disk is the primary?

And on which disk is GRUB situated?

Maybe is just a mapping thing because windows wants to be on the first hdd.

You can achieve that by altering your menu.lst by typing in console```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
For the backup.
Then you type for the altering```
gksudo gedit /boot/grub/menu.lst
```

And alter the windows settings in something like the following```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by raul_ on 2006-10-18
Ur computer is doing u a favour then :) But what do u mean with "wasn't allowed" ? GRUB won't show up?

---

