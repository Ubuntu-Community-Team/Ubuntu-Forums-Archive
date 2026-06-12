---
title: "Dual Booting with 2 SATA hdd"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by EllsworthT on 2008-02-15
Hello all, first time poster.

I just bought a dell XPS 420 with 1 320 GB SATA hdd. I also bought 1 320 GB SATA hdd aftermarket (Yet to be taken out of box).

I have Vista pre-installed on the one hard drive that is in the computer right now.

My goal is to have Ubuntu (Gutsy) installed on the second aftermarket hdd. I want my computer to prompt me for which OS to open upon startup.

Please walk me through, step by step, in how to install the hard drive and format it with Ubuntu.

Also: Is there anyway to have a third hdd that stores all of my files, etc. and would than be accessible through both OS's. (AKA save an .xml file to third hard drive and have it accesible in both Vista and Unbuntu or is this attainable with the above setup somehow.)


Thanks

-Ellsworth

---

### Post by Golem XIV on 2008-02-15
Download and burn the Ubuntu Desktop CD, stick it in the CD drive, boot from it (set the BIOS to boot from CD first).  Wait for the system to load.  Play a bit with it, make sure everything works; if it doesn't, make a note of it and look in these same forums to check if there is a solution.  Note that the Live CD system will be a lot slower than a "normal" system since it runs from a (intrinsically slow) CD.

Once you're happy that either everything "just works" or you feel confident that you can fix any eventual problems yourself, double-click on  the Install icon and away you go.

The installation will hold your hand for you, but there is one important thing to note:  You will be presented with a choice of drives to install.  Select the one that does NOT have Windows on it, otherwise it will erase and overwrite your Windows system.

This may be a bit tricky if both drives are the same size, but the Windows one will probably have a good chunk of storage used (especially if it's Vista!).

<edit>Forgot to mention that the SATA interface only supports 2 drives.  Unless you have 2 SATA interfaces and/or additional IDE interfaces, 2 drives is all you get.</edit>

---

### Post by EllsworthT on 2008-02-15
Thank you.

---

### Post by daryncox on 2008-02-15
I did the same steps as Golem XIV provided on my computer last night. The only difference being my machine had XP installed on the first drive and now Gutsy on the second. Everything works exactly as I wanted it to with Grub giving me the option of which OS I want.

---

