---
title: "Second Hard Drive"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-11-27
I am already running Ubuntu, Gutsy Gibbon as my default OS but i want to install a second Hard Drive to run a Windows OS. Does anyone know of or could provide a painless tutorial for an old n00b please. Thanks!

---

### Post by taurus on 2007-11-27
When you install windows on your second harddrive, it will overwrite GRUB so you won't be able to boot Ubuntu again.  However, you can reinstall GRUB to MBR without reinstalling Ubuntu so you can boot Ubuntu and windows anytime you want.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by anaconda on 2007-11-27
I would disconnect the ubuntu hd, and then install windows normally to the other hd. Then after installing windows I would add it to ubuntus bootloader. (assuming here that ubuntu is on the hd that boots first..)

---

### Post by philinux on 2007-11-27
You could also disable your first hard drive in the bios so windoze is only allowed to see the second hard drive. That way it cant overwrite grub.

Then re-enable the drive via the bios.

---

### Post by Gutti on 2007-11-27
do this: [http://www.jplawrence.us/mywiki/DualBootLinux](http://www.jplawrence.us/mywiki/DualBootLinux)

---

