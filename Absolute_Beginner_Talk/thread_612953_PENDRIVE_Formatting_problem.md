---
title: "PENDRIVE Formatting problem"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by hskb16 on 2007-11-14
I am not able to format my pendrive..If i press ctrl+a and Shift+del  .....none of the files r getting deleted .Furthermore i tried cd /media/NAME and rm * in the terminal.....But none worked ...
I also see these LOCK icons on my folders in the pendrive......
i ws able to copy and successfully run some songs from my pendrive ...but i am not able to delete anything......[IMG]http://img441.imageshack.us/my.php?image=screenshotsb4.png[/IMG]

Is it because of  a problem with my pendrive? i hv enabled read n write options for internal and external devices  NTFS config tool.....

---

### Post by timcredible on 2007-11-14
gparted will format a flash drive

---

### Post by hskb16 on 2007-11-15
gparted is not detecting my pendrive .What should i do ? i hav named it as HSK(my pendrive) ...shld i be able to see tht?

---

### Post by powder on 2007-11-15
1.  Unmount the drive and remove it
2.  System -> Preferences -> Removable Drives and Media
3.  Uncheck top three checkboxes under "Removable Storage"
4.  Plug the drive back in
5.  Open GParted and select the USB drive in top right corner (likely /dev/sdb)
6.  Right click -> Format to...
7.  Apply
8.  Remove the drive
9.  System -> Preferences -> Removable Drives and Media
10.  Check top three checkboxes under "Removable Storage"
11.  Plug in the drive

---

### Post by harshask on 2007-11-22
how do i enable WRITE permissions for my PENDRIVE??? I can write to my pendrive in other OS's i am having ..But not in ubuntu!!! ...:confused:

---

