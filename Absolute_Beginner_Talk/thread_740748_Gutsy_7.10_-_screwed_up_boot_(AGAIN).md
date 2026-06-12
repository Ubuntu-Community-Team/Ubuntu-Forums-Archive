---
title: "Gutsy 7.10 - screwed up boot (AGAIN)"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Thanh-BKK on 2008-03-31
Hello :)

After some help from other sources i managed to get an almost perfect Gutsy 7.10 system running - ALMOST perfect because the splash screens at startup and shutdown weren't there. So i found a solution for that, fixed it - shut down worked ok (WITH splash screen!) but now it won't boot anymore.

I get this error:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Now i have a little experience with Ubuntu and SuSE so i'm not an absolute newbie to Linux but this one has me cold. "Recovery mode" fails with the very same error, so i can't even get a command line.

It seems the problem is with the boot file in the "grub" folder - the one ending in .lst (sorry i'm on a Windows machine now, at the office, and the broken Linux box is at home) because when it boots, i have an option there to edit boot commands, and i see there something like 

"root=UUID=2465435465" (long string of numbers) instead of "root=/dev/hda0"

So i tried to edit that but for some reason it always reverts back to these UUID and long-number things (there is no "save" option, only "exit"). 

Booting from the live CD i can access the file system, there's nothing wrong with the HDD or any of the files but i have "no permissions" to edit any of them, and even "no permissions" to backup, i.e. copy/paste the "home" folder to a thumbdrive before re-installing the OS from scratch (yet again). 

Can anyone here please advice me on how to access the HDD from a command line (terminal) while booted into the live CD, then how to edit the relevant files and SAVE them? 

Is there a possibility to perform a "repair install" like under Windows? I think my installed system is still very much ok if not for that knackered boot file. Something like "fdisk /mbr" under Windows. 

Or should i just wait for Ubuntu 8.04 to be available and start from scratch with that one? 

Best regards......

Thanh

---

### Post by swoll1980 on 2008-03-31
use a live cd mount the hard drive then enter into the file and alter it that way

---

### Post by Thanh-BKK on 2008-03-31
Hi :)

Thank you for the reply. But as i already wrote - this fails because when i am on the live CD i do "not have permissions" to alter any file from the installed system. At least not thru the GUI (i can "edit" the file there but it refuses to save it for the "no permissions" reason).

If you could let me know how to do so from a command line? I.e. how do i get to the file in question, i know it is in the folder /boot/grub but when booted from the live CD, i need to put something in front of it (/dev/hda0/??) which i don't know. 

Best regards......

Thanh

---

### Post by prismpirate on 2008-03-31
Open the terminal when on the live cd and enter:

```

gksudo nautilus

```

Should open nautilus as root, try editing then. :)

---

### Post by Thanh-BKK on 2008-03-31
Hi :)

Thank you very much, i will try this when i am back home (now still at work for the rest of the day). 

Kind regards.....

THanh

---

### Post by erginemr on 2008-03-31
> **prismpirate said:**
> Open the terminal when on the live cd and enter:

```

gksudo nautilus

```

Should open nautilus as root, try editing then. :)

This should work, but you can also consider downloading and burning the Ubuntu Alternate CD, which has a recovery console mode (similar to the one in Windows XP) whence you can mount your hard drive and edit the files therein.

---

