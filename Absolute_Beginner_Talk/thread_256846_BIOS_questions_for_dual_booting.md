---
title: "BIOS questions for dual booting"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by cyntrelle on 2006-09-13
Hello!

I'm not new to Linux, but I am new to Ubuntu and to SATA drives.  I have been reading the past posts about dual booting with two drives, which is what I want to do, but I'm still
trying to figure out if my 'plan' to install will work, once my new SATA drives comes in the mail. 

I have a Dell Dimension, with an IDE drive currently installed with Windoze XP.  I would *like* to install Ubuntu on the new SATA drive I just bought (I have SATA capability on my motherboard) and I would like to have GRUB on the SATA drive, so as to not disturb delicate Windoze.  

My question (finally) is this:  in my BIOS, I see the SATA listed in the hard drive config. listing (currently as OFF because there is no drive there, yet), but I do NOT see the SATA drive as listed in the 'boot from' listing (or whatever it's called - the place where I can select to boot from 'hard drive C' or 'floppy' or 'CD-ROM').  This may be a "it depends" question, but, does anyone know if this likely means my BIOS does not allow for me to boot directly from a SATA drive, once a drive is in there (provided of course I configure it right)?  For instance, I don't have a floppy drive currently installed, yet it gives me an option to boot from floppy in the list of options, but tells me there is currently no floppy drive installed.  Not so for SATA. 

And if I HAVE to boot from the IDE WIndows drive, what precisely do I need to do to GRUB, which would then need to be on the Windows drive, so that I can select which drive to boot from on startup? 

Hope this makes sense, what I'm asking.  Thanks!

Cyntrelle

---

### Post by kidders on 2006-09-14
Hi there,

If you ask me, it would be inconceivable for your BIOS not to let you boot from an SATA disk ... I can't see why the I/O interface it happens to be using would make any difference. The idea that you simply couldn't boot your computer without at least one IDE disk would be silly.

I'm sure everything will work fine for you :-) but, as your post suggests, it might be smarter to put the bootloader on the disk that *doesn't* have Windows on it!

---

