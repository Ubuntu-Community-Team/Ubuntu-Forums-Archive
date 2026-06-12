---
title: "lock-up during Live load possibly ATI Radeon issue"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Charles-2007 on 2007-02-18
Hello attempting an installation of Edgy on a Compaq Presario 1800 laptop with a blank drive.  I have been experiencing a brown screen of death.  Tried the Dapper version with the same result.  Never get a successful load.  Searched for bugs related to the components of this Intel-based laptop and saw numerous reports of similar events with ATI Radeon Mobility graphics.

On boot of the CD I then edited the command line as recommended via F6 (I think that's the key) and deleted "quiet-splash" and substituted "break=bottom".  to get to initramfs where I entered "chroot /root nano etc/X11/xorg.conf" and successfully edited out ATI to "vesa" as recommended in the bug fix 59618.  I confirmed this editing.

Exiting this menu I saw a line that the system was loading the Gnome interface and then... brown screen of death.  OK maybe it is orange.  I note that the cursor locks up too.  I can't hit control alt F1 successfully either.

Any thoughts?

Bummer.  I'm stubborn and I'm going to try the alternative installation CD (haven't tried that yet).  I also wondered about the formatting of the drive (which had been erased and reformatted as FAT32) so I downloaded Gparted (a fantastic program!) which loaded fine and formatted the drive to ext3 -- but that didn't help.

---

### Post by BarfBag on 2007-02-18
Have you tried installing it with the text-based installer?  It's very easy to use, so no need to worry.  I believe it's the second option on the boot menu.

If that doesn't work, I recommend trying the alternate CD.

---

