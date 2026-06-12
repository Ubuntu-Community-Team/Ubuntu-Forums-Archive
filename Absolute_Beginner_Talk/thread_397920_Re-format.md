---
title: "Re-format?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by hulland on 2007-03-31
I have tried 7 differnt versions of Linux this week, now decided which one I want to install, I need to remove Ubuntu--can easily wipe the volume off, but can anyone tell me how I get rid of the dual boot part of the MBR? Will it go with Ubuntu ( cant be that simple?) Thanks for any help.

---

### Post by 1/0 on 2007-03-31
Are you asking how to remove what's in the MBR (for instance to install Windows) or how to edit the boot loader (GRUB/LILO)?

---

### Post by hulland on 2007-03-31
I am asking how to put my system back as it was before I tried Ubuntu--
--without re-installing windows of course..

..am I to assume I have to delve into the MBR or is there a simple way ( They don't tell you about all these problems BEFORE you try Ubuntu ! he he he ) any help appreciated..

---

### Post by 1/0 on 2007-03-31
If you want to remove GRUB or LILO from the MBR, then you can do this by doing:

```

fdisk /mbr

```

It will clean the MBR. That way you will not boot via GRUB but Windows. [This page]("http://support.microsoft.com/kb/q171611/") explains how to do it from Windows. 

Now, I don't know what you had installed before Ubuntu but assuming it was only Windows the above should do fine. If you had other OSs and want to twiddle with GRUB to do a dual boot the above will be very bad.

---

### Post by hulland on 2007-03-31
Many, Many thanks I/O--this is EXACTLY why I am giving up on Linux--this routine should be available in the built-in help in Ubuntu!!! Talk about an eliteist sytem--many thanks for taking the trouble to explain.. will go off and try..

---

### Post by 1/0 on 2007-03-31
It is actually built in on both the CD and the installation. 

The thing with GNU/Linux is that you can find solutions and get help with almost everything but one has to first search for info. There are more and better guides/howtos on how to uninstall GNU/Linux and go back to Windows. I'm just saying this if you want to give Linux another try in the future. Anyway, I'm glad that the problem seems to be solved.

---

