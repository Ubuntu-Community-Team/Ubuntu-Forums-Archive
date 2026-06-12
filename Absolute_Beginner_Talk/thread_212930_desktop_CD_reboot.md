---
title: "desktop CD reboot"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by sut07 on 2006-07-10
alright, i feel ridiculous for having to post this, but:
i burned the CD, loaded it up, it said i just need to reboot the computer and the linux demo would automatically start. so, i reboot the computer (WinXP) but nothing happens, WinXP loads as normal. i know the CD works, and i know the CD drive works, i'm really tired and confused. thanks.

---

### Post by melissawm on 2006-07-10
First of all, which cd did you burn? A Live CD or an install cd? I'll be glad to help you if you give me more info...

---

### Post by T700 on 2006-07-10
Check the boot sequence in the BIOS and make sure it is set to boot from the CD.  You did burn the ISO and not just copy it, right?

Paul

---

### Post by croak77 on 2006-07-10
Edited. Beaten to the punch.

---

### Post by Brunellus on 2006-07-10
are you absolutely sure that you burned an image, and not merely a disk with an iso file on it?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by sut07 on 2006-07-10
i burned the live CD, or the one where you can just use w/o having to change anything, the easiest one. i already set the BIOS so the CD would load first, no luck. i just realized though, this comp only has 128MB RAM. maybe that's the problem?

---

### Post by sut07 on 2006-07-10
i think i burned it correctly. i just d/l it, and when i clicked the icon on my desktop it automatically loaded up my CD burner and everything was ready to go, i just needed to click burn. is there anything else i need to do? i don't think this is the problem, cuz after this i loaded the CD and it said to use it all i had to do was reboot. hmm. thanks for the help everyone, much appreciated.

---

### Post by Brunellus on 2006-07-10
in Windows, when you pop the burned cd into the drive, what do you see?

If you only see a disk with an an iso file in it, you've burnt it wrong and should follow the directions on the wikipage I linked.  If the BIOS allows booting from the optical drive, you should be booting, which leads me to believe you've burned an unbootable disk.

---

### Post by sut07 on 2006-07-10
i'm not sure what an ISO file is exactly, i'm reading the linked page right now, but when i load the CD there are a bunch of files and folders, for example: .disk, casper, dists, isolinux, pool, programs, bin, disctree, install etc etc... you're probably right.

---

### Post by Brunellus on 2006-07-10
OK, good, you've burned the iso correctly.  

perhaps you need to hit a key while the machine is booting up to knock it out of its usual routine and force it to boot from one device or other.

---

### Post by sut07 on 2006-07-10
ok, any suggestions on what to hit? maybe just punch my computer? jk. thanks for the help, i'll keep trying.

---

### Post by T700 on 2006-07-11
> **sut07 said:**
> ok, any suggestions on what to hit? maybe just punch my computer? jk. thanks for the help, i'll keep trying.

Please post the make/model of the computer.

Paul

---

