---
title: "Installation CD won't boot"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by bobaj on 2006-09-19
I am an absolute beginner.

I'm trying to install Ubuntu on my desktop. I load the CD and start the PC, it will not load Ubuntu - the computer ends up starting WinXP.  Unnder WindowsXP, it will load the demo from the CD.  However I can not get it to boot to the CD.  I've tried versions downloaded from the website and the CD from ShipIt.  The CD from ShipIt loaded onto my laptop.  Any Suggestions?:frown:

---

### Post by bodhi.zazen on 2006-09-19
Is your BIOS set to boot from the CD-ROM prior to the HD ??

---

### Post by bunnynuts on 2006-09-19
Check your boot order in BIOS Make sure that you boot from your cd or dvd drive before the hard drive

---

### Post by bobaj on 2006-09-19
Thanks for the suggestion.  I had set the boot drive to the CDROM.  However with your suggestion, I went into to the BIOS and turned off booting from the hard drive, and that worked.  Thanks for the help.

---

### Post by wakaimono on 2006-09-19
I am having a similar problem. BIOS is set to boot cd 1st then HDD. The cd just sits there and does nothing. If I eject the cd, the HD kicks in and loads GRUB.
CD load on my desktop, but no longer on the laptop. Once Ubuntu is loaded from the HD, the CDROM is mounted and I can access the CD.
Is there a way to install from the cd without booting it, like from the command line?

---

### Post by bobaj on 2006-09-19
I turned off boot to the hard drive and loaded the CD.  After the program gets loaded, I will go back into the BIOS and turn on boot from the hard drive.  I'm hoping that this will work - don't see any reason why it wont.

---

