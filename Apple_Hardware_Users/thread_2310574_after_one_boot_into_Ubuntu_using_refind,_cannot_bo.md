---
title: "after one boot into Ubuntu using refind, cannot boot into OSX"
date: 2016-01-20
forum: Apple Hardware Users
---

### Post by 7elEvan on 2016-01-20
Hello!  First, I've never used any Linux system before.  I recently installed refind on my Macbook Pro 5,5 so I could dual-boot OSX (El Capitan) and Ubuntu 14.04.  Refind worked great before the Ubuntu installation.  I changed the HD size to account for the Ubuntu partition and left the OSX recovery disk in place as well.  After the Ubuntu installation, I rebooted the system and refind worked great, I chose the Ubuntu partition and it booted.  However, now when I reboot my system, refind does not come up and it boots directly into Linux.  Well, I figured I could boot into the OSX recovery disk and set the OSX partition as primary for booting (read that somewhere), but holding down command+R does nothing...

Any help is appreciated!  Thanks!

---

### Post by howefield on 2016-01-20
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by BobUgh on 2016-01-20
Command-R *should* have booted directly to the recovery partition. Try holding "option" down while powering on, that might bring you into another(?) boot manager. OSX should be a choice along with recovery and maybe even refind

---

### Post by este.el.paz on 2016-01-20
> **BobUgh said:**
> Command-R *should* have booted directly to the recovery partition. Try holding "option" down while powering on, that might bring you into another(?) boot manager. OSX should be a choice along with recovery and maybe even refind

These are good suggestions . . . also, I think I've posted somewhere on the sub-forum, that rEFInd seems to "learn" your choice and offers it again . . . so, indeed, trying to boot with option key should show you OSX . . . pick that.

e...

---

### Post by 7elEvan on 2016-01-20
Thanks for the replies!  I have tried booting again using option+r, and I still get nothing.  I press it when the start-up chime sounds, and soon after the screen goes black, then purple, and I'm in Ubuntu.  I checked to make sure I didn't overwrite the recovery partition when I installed Ubuntu, and lsblk reveals a partition that is 620 MB, so about the right size (I think it said 650 when I was installing Ubuntu in the free space on my HD).

---

### Post by este.el.paz on 2016-01-20
> **7elEvan said:**
> Thanks for the replies!  I have tried booting again using option+r, and I still get nothing.  I press it when the start-up chime sounds, and soon after the screen goes black, then purple, and I'm in Ubuntu.  I checked to make sure I didn't overwrite the recovery partition when I installed Ubuntu, and lsblk reveals a partition that is 620 MB, so about the right size (I think it said 650 when I was installing Ubuntu in the free space on my HD).

@7:

Just checking, here above you are saying "option+r"????  No, that would not be correct . . . "command+r" should get you to the recovery disk.  And, just "option" on reboot . . . maybe you need to be holding it before the chime . . . should get you to OSX boot manager . . . should show you the OSX disk, the recovery dsk . . . and possibly linux, labeled as "windows" . . . . [edit: but rEFInd should also show OSX as an option.]

e..

---

### Post by BobUgh on 2016-01-22
I have had better luck pressing the key[s] down before powering up, and continue holding them down until I see the screen that I want. And just "option" should give you a choice of going into your regular OSX or recovery, or possibly a 3rd choice that will eventually get you into Ubuntu.

---

### Post by 7elEvan on 2016-01-27
Thanks everyone!  Using the option key worked very well.  I'll try holding down the keys beforehand like you suggest as well, Bob.

---

