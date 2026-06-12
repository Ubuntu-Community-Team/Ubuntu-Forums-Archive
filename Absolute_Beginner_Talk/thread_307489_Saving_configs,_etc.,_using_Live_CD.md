---
title: "Saving configs, etc., using Live CD"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by jim-c-logger on 2006-11-26
I think I count as an absolute beginner even though I have been using Linux for several minutes now.  ;-)

I am in a "50 first dates" mileaux: I am using the "Live CD" version of ubuntu and have not found a lot of documentation on how to save things.  Every time I start the CD I have to reenter my email customizations, GAIM profile, etc.  I created 2 test docs using the OpenOffice programs, and they are gone as well.  I looked at the System > Admin > disks, and the only file systems mounted are /tmp, which explains why they are deleted when I shutdown.

How can I define a disk (and my preference is not to have to do a hard partition) that will keep my ubuntu set up info and files?

Would appreciate any pointers...

Jim

---

### Post by CatKiller on 2006-11-26
The whole point of the live cd is so that you can use it without affecting anything. You're supposed to install it if you like it, since then it will run better :)

I suppose you could use a USB drive to store things on if you're dead set against using the hard drive, but I've never done it.

---

### Post by Bloch on 2006-11-26
It must also be painfully slow to run ubuntu from the CD.

---

### Post by houstonbofh on 2006-11-26
You have two options.  One is that you can manually mount hard drive partitions RW.  This is a pain in the but, and involves a bunch of unix stuff a lot of new users find distasteful.  Or you can plug in a usb thumb drive.  It will automount when you plug it in, and show up on the desktop.  Then you can tar or untar your home directory if you want all the settings, or just save some files.

---

