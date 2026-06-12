---
title: "failed to create file system?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by redtendoned on 2007-07-15
Ready to install:

If you continue , the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSl1 (0,0,0) (sda)

The following partitions are going to be formatted:
partition #1 of SCSl1 (0,0,0) (sda) as ext3
partition #5 of SCSl1 (0,0,0) (sda) as swap

[B]I click install and it makes it to 15% where it is "Detecting file systems" and an error pops up:
Failed to create a file system
The ext3 file system creating in partition #1 of SCSl1 (0,0,0) (sda) failed.[/B]

I feel like a jerk not asking for help already without even successfully being able to install, but I figured with a community of this magnitude that someone may have been there, done that and could point me in the right direction.

Any help would be wonderful, thanks much!

-Chris

---

### Post by redtendoned on 2007-07-15
Forgot to mention...

I was running Windows XP Home edition and backed up all files I was interested in keeping to my 80 gig external. I want to wipe this 60 gig internal clean and solely run Ubuntu.

---

### Post by freebird54 on 2007-07-15
Well - it sure sounds to me lime an actual hard drive error.  Since you want it completely cleaned off anyway- do you have the utilities around still to have the HD format itself? (this should mark any bad bloacks off, and prevent recurrence on this part of your disk.)

Of course - it is also a warning that things may be going 'south' in the near future with this particular drive... :(

If you can't get it formatted by its own utils, you can partition around the suspected bad area as well....

---

### Post by redtendoned on 2007-07-15
Thanks for the quick reply!

I did a little digging around the forums. Found some advice to try booting Ubuntu in the safe graphical mode. I did so and ran the install accordingly. So far so good! (45% ish) I'll see what comes of this...I sure hope it works out, this is such an amazing platform and I can't wait to reap the benefits!

---

