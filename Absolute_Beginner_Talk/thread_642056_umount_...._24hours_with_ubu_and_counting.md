---
title: "umount .... 24hours with ubu and counting"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by nirvanadesign on 2007-12-16
hi jedi's

OK

i into the 24th hour with ubuntu and its great

just sorted my NVIDIA card and have skinned my desktop. I have played with cron and have  wrote a shell script.

I like it!

ok im waffling

when i boot Ubuntu i see drives on my desktop which contain my windows installation so i umount them and they vanish. I then drag over my backup partition so its handy. When i reboot this all goes back to the way it was originally. How can i make this a permanent set-up:popcorn:

---

### Post by macogw on 2007-12-16
Remove the lines referencing those drives from fstab using "gksu gedit /etc/fstab" in the terminal.  They will no longer mount automatically at boot.  You can also add a line for the backup partition, following the same format as other partitions.

---

### Post by nirvanadesign on 2007-12-16
thanks macogw

will give this ago

---

### Post by Paqman on 2007-12-16
Probably best to just comment those lines out, rather than remove them altogether. Also, always make a backup of fstab before editing it.

---

### Post by mpince on 2007-12-16
You may not want to totally remove the drive entry in fstab.

You could just modify it so it won't mount-- I think changing 'auto' to 'noauto' for that drive.

Here is a site that explains what the options mean:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

