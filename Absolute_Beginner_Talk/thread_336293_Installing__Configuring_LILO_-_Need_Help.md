---
title: "Installing / Configuring LILO - Need Help"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by jcq on 2007-01-11
OK, for a little background on why I need to do this, see my post here:
[http://forum.notebookreview.com/showthread.php?t=97762](http://forum.notebookreview.com/showthread.php?t=97762)

Short story: there's a conflict between the BIOS of my laptop and Grub which prevents access to CD/DVD drive in both Linux and Windows.

So, the solution apparently is to install LILO.    My question then is, how do I do that in Ubuntu?  Can I just use the package manger to get and install it?   I assume I have to edit lilo.conf, right?  Is that fairly straight forward?   Once edited, do I just run "lilo" to write it to the MBR?  After that it's the boot loader, and I don't have to do anything to Grub?

If anybody is able to give me explicit instructions as to the lilo.conf file, that would be most appreciated.    Mine is a dual-boot setup with XP on the primary partition, Ubuntu on the 2nd, and a 3rd for the swap.   

I see that there is a package for lilo-config for kubuntu that in theory makes this easier...  is there something similar for default Ubuntu (Edgy)?

Thanks in advance...

---

### Post by jcq on 2007-01-11
Oh, and one more quick question...   since I used XP's "fixmbr" command to restore full functionality to at least one OS, how do I get back into Ubuntu to do the LILO install?   I haven't actually installed anything yet in there, so I could easily just do another install, but that seems a little silly.  Can I boot from the CD and use that to boot into the linux install on my HDD?

---

