---
title: "Howto image/backup the Triple Boot?!"
date: 2008-04-07
forum: Apple Intel Users
---

### Post by api2001 on 2008-04-07
Hey folks,

finally I got to run my new triple boot MacBook having a very shortened MacOSX with 25 GB, a small 20GB Windows and the rest for Kubuntu Linux.

So my experience after 3 to 4 days installing, destroying, installing, destroying, installing right now tells me that I should think about a way to image/backup my triple boot system.

What is a good way to do that including backup of the partition table and booting stuff (EFI, GPT, MBR, ..?) and my other three partitions?
I think it would be good to have all three OS as separated images?!
The MacOSX boot CD disk tool would be quite nice, but I once did an image of my Windows with that and I just could not play it back to the same partition which is of course not what I want. So this would only work for MacOSX I suppose?!

Perhaps somebody has experience in this and has a great invention he would like to share with us? ;)

Bye bye,
APi

---

### Post by benanzo on 2008-04-07
It's pretty easy to backup your systems now that they're all installed and working nicely together.  It's a little tricky (and cumbersome) to try to grab the GUID/MBR of your disk since it may or may not work correctly depending on where your systems are installed.  My advice is to take backups from the second link below and then when you need to just restore them onto the appropriate partitions and the boot a LiveCD to reinstall grub, run gptsync (refits avail in universe) to sync the GUID/MBR, then run the Windows boot disk in repair mode to do fixboot/fixmbr.  That will restore you to where you were without worrying about making tedious backups of MBR etc.

Or you can just follow the first link to do full images of your disks/partitions.

How to image a disk (including MBR):
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

How to backup/restore Windows/Mac/Linux:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Good luck!

---

