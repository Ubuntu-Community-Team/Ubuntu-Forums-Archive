---
title: "black screen when i turn on visual effects"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by mhrpinca on 2007-12-28
Help i loaded Ubuntu,7.1.0 then loaded the KDE desktop, and Ubuntu studio, all was good,,,,,,
then i loaded Compiz cube thing? it worked i customized it to  to look the way i wanted it to and life was good. then i logged out and when i logged back in i saw the desk top back ground for a second then the screen went black and i had a small square in the upper left hand of the screen that showed part of the menu bar it was like i had a layer blocking the screen.when i pushed down on the scroll button i still had the cube and could rotate it but what ever desk top i rotated to i still had the same problem. turning off affects made it go away....... i've disabled and reinabaled my graphics driver (nvidia) i've uninstalled and reinstalled Compiz, i've also uninstalled the KDE desktop.
im new to Linux and Ubuntu.
also how do i uninstall and reinstall ubuntu on a multiboot system. with out messing up the grub and mbr? last time i tried the first part of the grub would load and then i was given an error 17 message. and had to use BIOS to get to my drives.

                      ?????????????thanks :confused:

---

### Post by mejy on 2007-12-28
It sounds like you've taken some pretty drastic steps and it'll be easier to simply reinstall than to fix it.  I'd guess the most likely fix is running the command ' rm -rf ~/.gconf/apps/compiz' - that will remove any desktop effects configuration changes you've made, which are likely to be the root of the problem.

I can't give you the specific reinstallation instructions for KDE since I use gnome and XFCE, but first you'll need to boot the live cd.  Then find the partition editor (I'm not sure which one will be installed) and unmount and delete all linux partitions.  Then run the install wizard as usual, tell it to use the free space and install the grub boot loader on the same place as before (probably the harddrive root).

Good luck!

---

### Post by markharding557 on 2007-12-28
reinstalling should not present any problem as grub will detect windows or any other o/s during your reinstall.
when you get to the partitioning point in the install,choose manual partioning,here you can select the mount points for your drives

---

