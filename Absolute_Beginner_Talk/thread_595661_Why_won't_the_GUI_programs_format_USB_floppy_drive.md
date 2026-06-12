---
title: "Why won't the GUI programs format USB floppy drives?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by lyndaj70 on 2007-10-29
Hi,

Why won't the GUI apps format a usb floppy drive?  I can format fine in command line, but can't format either using kfloppy or gfloppy.
:confused:
Just curious....

---

### Post by Henaro on 2007-10-29
Have you tried running them as root?  I have to run kino with gksudo to capture digital video.  So it may be the same.

---

### Post by lyndaj70 on 2007-10-29
Yes.  I get an error.

Changed my usb permissions by making a group called usbusers giving me read/write privileges and edited my 40.permissions.rules files to reflect that (had to do it to get virtualbox access to my usb), and while I have had no luck with gfloppy I can now get kfloppy to say that there is an error with mkdosfs.

I am going to guess it is because you have to force mkdosfs to format the whole drive by typing a switch

sudo mkdosfs -I /dev/sdb

and the gui apps don't have that switch built in...

... I have used the GUI for formatting floppies since I started playing with Linux years ago, but this is my first experience in Linux on a laptop with a USB floppy. All my others had been internal and they formatted with no problems.  It seems that this could be very frustrating for new users so I would like to figure out a solution, for myself and others.  There "has" to be a way to make the gui apps work, or else the little apps are worthless.  And running Windows in a virtual machine just to format a floppy in a gui is *not* an acceptable solution, though it does work (grin).

So the game is on...  :guitar:

---

