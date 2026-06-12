---
title: "Gutsy died in front of me..."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2007-11-05
I was surfing the web then minimized it to open a mini game. Before I opened the mini game, firefox closed. I tried to open System monitor to see if firefox is still running. Then, all of a sudden, the GNOME panels closed and everything hanged. 

I rebooted my PC again and found that GRUB showed an Error 17.
I used the Fiesty live CD and looked at the harddrive using GParted and saw that my Ubuntu partition is now an "unknown" and is shown in black.

I have no idea what to do since this is the first time I saw this.

My harddrive is a 120GB seagate. 3 Years old. My NTFS partition is still intacted.

I really need help on this one. I cant even open the Filesystem partition using the live CD.:(

And I'm really scared of reinstalling my Ubuntu again. My old one was extensively customized.

---

### Post by P4man on 2007-11-05
sound like your harddisk is dying or dead. You could try booting from the "ultimate boot cd" (google on it), and run the harddisk diagnostic program for Seagate.

Another (although faint) possibility: I had similar issues and random crashes and lockups and even grub trouble (error 17) with an Asrock dual VSTA 775 motherboard. Wat cured it for me, was going in to the bios and setting "IDE drive strength" from "low" (default) to "normal" or even high. Its worth pointing out that the Maxtor diagnostic program didn't find any problems even with drive stength set to low, but I sure did :)

---

### Post by dnns123 on 2007-11-05
I'm trying it now. But I really dont think its my harddrive cuz I can still access my other partitions.

---

### Post by P4man on 2007-11-05
that doesnt prove anything. The defect could well be in the Linux partition or partition table.

One more thing: you didn't change anything to the BIOS (startup order) did you ? Or using the BIOS boot menu can also cause havoc to Grub as it changes the disk order

---

### Post by dnns123 on 2007-11-05
I didnt touch the boot sequence. It worked fine yesterday. But today, it just hanged.... then *kaput*

---

