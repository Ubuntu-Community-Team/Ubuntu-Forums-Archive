---
title: "Make An External Cd-Rom Drive"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by koldphlame on 2008-02-24
i am have an old cd rom drive and am currently working on a laptop for someone who OS is messed up i was going to delete the partition and reinstall but the cd rom in the laptop  is messed up

**I NEED TO KNOW IF IT IS POSSIBLE TO MAKE ONE:confused:**

---

### Post by willmcgree on 2008-02-24
If it's an old internal CD-ROM drive (the kind that fits in a tower), you could just get a 3.5" external USB enclosure (as long as it's suitable) and use that.

BIOS tweaking (press Del, Esc or F2 or whatever - it'll tell you - at boot-up) is not that hard and nowhere near as scary as people think.

You need to check if USB-HDD is higher up in the Boot Priority (or Boot Order or similar) than Internal Hard Drive (or Internal HDD or IDE HDD or SATA HDD or whatever) so that the computer looks for something bootable on the CD before the hard drive.

Once you have that set up, save changes and reboot with the disc in the drive. Hopefully, Ubuntu will load and you'll see the menu.

If not, come back and let me know.

Hope that helps.
Will

---

### Post by Forrest Gumpp on 2008-02-24
This link is to a tip in the How To sub-forum.  The tip is titled ' HOWTO Boot from any .iso file without needing a working CD-ROM'.

It might not be exactly what you have in mind, but it may help you out.  [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

