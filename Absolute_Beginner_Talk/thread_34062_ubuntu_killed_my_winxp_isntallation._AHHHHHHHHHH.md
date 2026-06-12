---
title: "ubuntu killed my winxp isntallation. AHHHHHHHHHH"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by petesmc on 2005-05-13
Ever since installing (k)ubuntu my winXP isntallation is dead. Using grub, It tries to boot from it,it gets the WInxp loading screen but then tries to do a scandisk and restarts itself...this is realllly bad. Lucky i did back up my data, but my cd is 10000miles away.

---

### Post by codejunkie on 2005-05-13
did you mount and write to windows partition under ubuntu? if you wrote data to it, it might be hosed if not you might be able to use the windows cd and fixmbr from the recovery console, or reinstall grub.

---

### Post by Badrul Nazar on 2005-05-13
I had the same problem before. After installing Warty, Win XP cant load.

Go to google & search on changing Hard disk setting in CMOS (somehing about LBA)

1) During boot - press DEL (or equivalent)  to enter cmos setup
2) Find setting about your hard drive
3) Change to "LBA" mode
4) Save and reboot.

Hope it'll solve your problem

---

### Post by Jace on 2005-05-13
What do you mean by dead. Will it get to the point that it ask you for your username and password?  Any bluescreens?

---

### Post by petesmc on 2005-05-13
ok.

Heres some info:

I haven't mounted / read/  written windows partitions in Ubuntu.

I have a laptop which doesn't let me set the hard drive mode in bios (won't even tell me if it's LBA or normal mode)

When windows boots, I get the Windows XP loading screen then it tries to do a scan disk but i get an error like "unable to find chkdsk". Then the computer restarts.

I will try to fixmbr later when i find an XP cd to use.

Here's what my fdisk says, incase anything weird is going on. Partition 1/5 are my windows C/D:\ drives.
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  17  Hidden HPFS/NTFS
/dev/hda2            2433        3568     9124920    f  W95 Ext'd (LBA)
/dev/hda3            3569        4799     9888007+  83  Linux
/dev/hda4            4800        4864      522112+  82  Linux swap / Solaris
/dev/hda5            2433        3568     9124888+   7  HPFS/NTFS


``` 

I don't know where to find the grub config file so i can't post that....

---

### Post by az on 2005-05-13
Post your: /var/log/debian-installer/partman

---

### Post by petesmc on 2005-05-13
Ok i've attached it as an attachment.

---

