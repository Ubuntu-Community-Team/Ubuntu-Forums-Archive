---
title: "Install won't detect LG DVD writer"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by nedsnow on 2006-12-21
Hi folks,

I am brand new to Ubuntu (but not Unix), and am having problems attempting to install. Ubuntu cannot detect my LG DVD Writer during the install, even though it boots from it, so I cannot proceed past the CD Mount step. I have gone through the forums and seen many others with the same problem, some with exactly the same drive, but no replies which offered a working solution to the problem.

I have tried both the Live CD and the Alternate CD, and neither work. Both CDs work fine on a Dell computer that I have, so it is not the CD.

My hardware is:
Asus P4S800 MB, SIS chipset  (No SATA! It is not a SATA problem!)
ATI Radeon 9800 Display (It is not a display problem! It cannot detect the CD!)
1GB Ram.
80GB Drive on IDE0/Master
120GB Drive on IDE0/Slave
LG DVD Writer on IDE1/Master

If I go to a shell and type "mount -tiso9660 /dev/hdc /cdrom"
it says Invalid Argument.

This command works on the Dell machine (if I unmount it first :D )

"list-devices cd" gives /dev/hdc

Is there any solution in sight? Anyone provide a clue?

Thanks in advance for any help.

Ned

---

### Post by JayTee on 2006-12-21
I'd first check on LG's website to see if they have a firmware update. Sometimes the bios info on the drives aren't quite what they should be. I have a friend who had a similar problem with a DVD writer he got from Dell as an upgrade to his Dell system.

---

### Post by meng on 2006-12-21
> **nedsnow said:**
> If I go to a shell and type "mount -tiso9660 /dev/hdc /cdrom"

It's:
mount -t iso9660 /dev/hdc /cdrom
with a space after the -t
but I'm not sure this will solve your problem, since you probably still need to boot from the CD. If the firmware update thing is not an option, perhaps ... another distro?

---

### Post by nedsnow on 2006-12-21
Thanks, but I'm pretty confident the space isn't significant.

From my original post:

>>This command works on the Dell machine (if I unmount it first  )

---

### Post by jvc26 on 2006-12-21
I thought you needed the space lol, have you tried with just in case? might be a pain to go to a load of trouble if that was all it was.
Il

---

### Post by 3rdalbum on 2006-12-21
Which model of DVD burner do you have?

---

### Post by nedsnow on 2006-12-22
Bios reports HL-DT-ST DVDRAM GSA_4163B

---

