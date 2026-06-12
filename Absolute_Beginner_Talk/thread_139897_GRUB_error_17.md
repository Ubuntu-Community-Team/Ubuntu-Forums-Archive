---
title: "GRUB error 17"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-05
Curiousity has landed me into trouble.

I have Win XP (/dev/hda1) and Ubuntu 5.10 (/dev/hda8). I was resizing partitions using GParted LiveCD, and I did so successfully. But upon restarting the computer, I get GRUB error 17 during booting.

I had no option but to re-make the mbr in Windows so I can load windows. I have the install CD for Ubuntu ready with me. Yet I dont want to re-install the whole thing. How can I simply re-make GRUB?

---

### Post by cotcot on 2006-03-05
This way : [http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed)

---

### Post by JoshHendo on 2006-03-05
Ok. If you want to replace the mbr for windows, put in the windows boot floppy (if using 2k or lower), go to the command prompt and type in fdisk /mbr .
If using XP (which you are :P), put in your XP cd, go into the command prompt and type in fixmbr or mbr . I can't remmeber which. As for error 17, that means:

Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by AtinLango on 2006-03-05
I had already ressurected Windows by fdisk /mbr. Thats what I meant in my original post.

I tried the link suggested by cotcot to re-install Grub and got very good, but delicate instructions. At a point along the way, I presses Y rather than N and things backfired. At the end of it all I was forced to make a clean re-install of Ubuntu. Am moving on.

---

