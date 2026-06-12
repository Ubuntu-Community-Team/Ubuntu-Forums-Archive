---
title: "bootable cd problem"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by zexoc on 2005-11-16
hello peeps

ive just downloaded and unrar'd the live ubuntu 5.10 cd and then burned it (as a bootable disc) onto a cd using nero. 

the problem at the moment is that the pc wont boot Ubuntu at all. 

i've tried just about everything: 

changing the boot sequence in the BIOS to floppy > cdrom > hdd. 

putting Smart Boot Manager onto a floppy drive and then tring to boot, this gives me a 'remove any disks and press any key'.

i would be grateful if someone would help.

---

### Post by lutrafobic on 2005-11-16
When you burned the cd did you use the "Burn image" option?

[IMG]http://www.lutrafobic.com/forum_pics/nero.jpg[/IMG]

---

### Post by zexoc on 2005-11-16
lutrafobic, i used nero express 

[ATTACH]3625[/ATTACH]

---

### Post by zexoc on 2005-11-16
that screenshot was a little small, i'll try again

the forum shrinks jpegs

---

### Post by lutrafobic on 2005-11-16
That options is only for creating the bootsector on your own, you shouldn't do that.
The .iso file contains everything you need so don't mess with the bootsector on your own, you must likley will just end up with the kind of problems you have now.

In the express mode, isn't there an option for "Burn image" ?

Or perhaps it's called "Disk image or Saved project" ?

---

### Post by zexoc on 2005-11-16
i've always been unable to boot from floppy or cd, even before trying to demo Ubuntu. any suggestions on how to boot from floppy or cd?

hmm, i dont think i was supposed to unrar the iso, i'll redownload it.

---

### Post by lutrafobic on 2005-11-16
You should not unpack the .iso file.
The .iso file is a so called "image" file, which contains the proper instructions about what file and were to put it on the CD as well as how to make a correct bootsector on the CD. The instructions are meant for your burning-software, not for you.
So if you get the .iso file again and use the "Burn image" -mode instead of trying to make your own CD, you should get a working, bootable Ubuntu-CD.

As for your booting problems you computer should have a BIOS option to boot from CD, when the boot-option in you bios is set to check the CD BEFORE the Harddrive AND you have a correct CD, the installation should start.
Note: If it doesn't boot and you know you got the CD right, try diffrent settings in the BIOS, perhaps; CD-FLOPPY-HARDDRIVE  or  FLOPPY-CD-HARDDRIVE, anyway, try different settings.

chears

---

### Post by zexoc on 2005-11-16
ive tried changing the boot sequence but the pc always ends up booting from the hard disk.

---

### Post by lutrafobic on 2005-11-16
Yes, but as I understood it you've not burned the CD correct.
If you try starting with a CD that doesn't have a correct boot sector the computer will just take the next in line, tous the Harddrive.

So if you just burn the cd proper it most likley will boot from the CD, when you installed Wintendo XP once, didn't the boot-from-cd-thingy work then? Otherwise how did you install XP?

---

### Post by ormus on 2005-11-16
in win2k,
i saved the ubuntu iso file to a folder on my hdd and then right clicked on it, then "open with" nero. then burn it. works everytime.
trying to burn it from within nero the usual way results in errors like yours.

---

### Post by zexoc on 2005-11-17
i downloaded it again and burn it as an image this time, but my pc still wouldnt boot from it. i think its to do with the bios. 

so i tried it on another computer (P4  2.4) and it worked.

---

### Post by zexoc on 2005-11-18
I finally sorted it out, what I did was put the hdd in the secondary ide slot, and the cd drive on the first, and it did boot from the cd.

---

