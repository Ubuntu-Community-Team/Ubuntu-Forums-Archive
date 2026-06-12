---
title: "Ubuntu Booting Problem"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mr_arunkumar on 2007-06-18
I am sure that thre would have been several queries in the past regarding this , i did search the forum and tried multiple solutions but nothins worked.

The problem is that i Installed Ubuntu 7.04 in PC (P3/40GB HDD-IDE) as single installation , but after nstallation the GRUB does not load and gives error 25 after displaying"GRUB Loading , Please Wait " message for some time. I was able to load ubuntu by using Super Grub Disk and that works like a charm but when i reboot & try to boot with HDD i end up with the same error.

I  have tried the various solutions like re-installing GRUB , Fixing GRU with Super GRUB disk etc but till this is not resolved. I would appreciate if you can walk me through the process for rectifying this issue. 

I like Ubuntu & would not like to miss the opportunity of having a clean install due to a minor boot issue ;)

Thanks,
Arun

---

### Post by candtalan on 2007-06-18
I see that grub error 25 is
=================
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk.
=================

is your hard drive configuration ok? - does the bios report the hard drive correctly (40GB)? Some early bios's had a limit of less than 40GB, although when I had that problem I think the error was a different number.
Is the hard drive jumper ok (master if a single drive)?

The boot sector is apparently referring to a place in the drive and grub is having a problem reading from that place. 
When you reinstalled grub how did you decide where locations were(hd0,0) or similar?
sda(0, 0) 

just a thought - recently the hda is becoming referrred to as sda (types are merging or something) and I had a problem in my PIII laptop with confusion about either hda or sda.

hth

---

### Post by mr_arunkumar on 2007-06-18
Thanks for your response. I had re-installed GRUB after finding the /Boot/Gtage1/Grub and installed in the same partition. But as you mentioned this has to do something with the BIOS / HDD setting only as i am able to select the GRUB from the Super GRUB Disk and then Ubuntu loads. Let me do some checks on my HDD  & BIOS setting. 

Incase you are aware of the process to set BIOS to recognize 40 GB HDD then let me know . else i need to google it & then try fixing it. 

Thanks !:D

---

### Post by mr_arunkumar on 2007-06-18
Thanks for your response. I had re-installed GRUB after finding the /Boot/Grub/Stage1 and installed in the same partition. But as you mentioned this has to do something with the BIOS / HDD setting only as i am able to select the GRUB from the Super GRUB Disk and then Ubuntu loads perfectly. Let me do some checks on my HDD  & BIOS setting. 

Incase you are aware of the process to set BIOS to recognize 40 GB HDD then let me know . else i need to google it & then try fixing it. 

Thanks !:D

---

