---
title: "uninstallation"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by OLT on 2006-08-16
since i`ve been using linux more and more i decided to by another hardrive and have 1 hardrive for linux and one for windows so i was going to simply wipe both drives but before i do that I need to know something what will happen to grub if I delete the linux partition on my hardrive will when I reinstall have 2 grub bootloaders for some reason or some strange occurence like that. Thanks for looking at this post. On the same note if i use gparted to wipe the entire drive would grub still show up when i tryed to boot or installed a none ubuntu os on it. Just a thought

Thanks for answering

---

### Post by kebes on 2006-08-16
During a grub install (which will occur automatically if you reinstall Ubuntu), it will auto-detect bootable partitions and add them to the "/boot/grub/menu.lst" file, which means they will show up at boot time.

So if you don't format/erase the older Ubuntu install, and install a new Ubuntu on a second hard drive, you will have 2 Ubuntus listed in your grub list (plus your windows install also). This is probably not what you want.

I believe that if you format/erase the current install, and perform a new installation, grub will figure it out and list the proper number of entries.

However even if it makes a 'mistake' it's no big deal. You can edit the text file I mentiond (/boot/grub/menu.lst) and control exactly what options are shown during boot. It's entirely under your control.


You said that you wanted to wipe both drives and reinstall everything. If you do this, then grub will be fine at the end of everything. If you are reinstalling Windows and Ubuntu, I recommend installing Windows first, and Ubuntu second. Windows will change the master boot record (MBR), and then when you install Ubuntu, it will put grub back into the MBR, and everything should work properly.

---

