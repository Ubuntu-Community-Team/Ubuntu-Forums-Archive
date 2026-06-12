---
title: "GRUB geez..."
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by pwrntspd on 2007-02-23
For some weird reason it seems as though GRUB hasnt been installed on my HD with ubuntu.  At start up all i get is GRUB loading...please wait...  And when i tried using the super grub disk it couldnt find grub on my partition.  I only have 2 partitions, one swap one linux but its meant to be an ubuntu pc. Whats going on? can i fix it? Ive tried to load Ubuntu multiple times, ive also tried to use live CD and terminal to fix the problem but to no avail, probably because i dont know whats wrong.  Ive downloaded the ISO multiple times, both types from different servers, i even tried xubuntu. still nothing....please help, im frustrated...

---

### Post by chewearn on 2007-02-23
It could be you have a BIOS, which has MBR antivirus protection feature enabled.  Look into your BIOS setup to see if this is true, and if so, disable it before installing ubuntu.

---

### Post by xyz on 2007-02-23
You did try thsi?
[How to restore Grub from a live Ubuntu cd.]("http://www.ubuntuforums.org/showthread.php?t=224351")

---

### Post by pwrntspd on 2007-02-23
> **AstalaVista said:**
> It could be you have a BIOS, which has MBR antivirus protection feature enabled.  Look into your BIOS setup to see if this is true, and if so, disable it before installing ubuntu.

Well if it has antivirus i cant find it...

---

### Post by pwrntspd on 2007-02-23
> **xyz said:**
> You did try thsi?
[How to restore Grub from a live Ubuntu cd.]("http://www.ubuntuforums.org/showthread.php?t=224351")

Yeah i tried that, didnt help.  Infact thats what made me think that grub wasnt installed at all.  I tried the long way by mounting it to my HD and when i checked to see what files were in that partition GRUB didnt come up whereas it did in the explanation.  Im thinking that maybe it didnt install grub at all, or not all of it.

---

### Post by nonewmsgs on 2007-02-23
i actually had this same problem.  im still not sure why, but in BIOS i did a set all to defaults, and there it was.  if anyone knows why that worked im all ears, but happy it did.  until then it's a magic move that might work. :)

---

### Post by pwrntspd on 2007-02-23
> **nonewmsgs said:**
> i actually had this same problem.  im still not sure why, but in BIOS i did a set all to defaults, and there it was.  if anyone knows why that worked im all ears, but happy it did.  until then it's a magic move that might work. :)

Ill try that, the other thing it might be is the HD is in CHS mode...weird...needs to be LBA for linux...just need to fix that...any ideas?

---

