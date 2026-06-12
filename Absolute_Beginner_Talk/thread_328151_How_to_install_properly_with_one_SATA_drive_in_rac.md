---
title: "How to install properly with one SATA drive in rack?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Raffael on 2006-12-30
Hi!

I'm a beginner at Linux systems so I've encountered a problem before installing it on HDD.

My situation looks like this:

I have 2 HDD
-1 SATA II drive in a rack with Windows XP
-1 IDE drive without any system

I would like to install Ubuntu on the IDE drive. The problem is that I want the bootloader screen to occur only when my SATA drive (with Windows XP) is in the rack.
When the rack is empty Ubuntu should start-up without any questions (like: which system to choose)

Maybe I should place GRUB on SATA drive (the one in the rack) so that when it's not present my PC will find only one drive with OS (I may be wrong)

Is it possible to do?

Thanks in advance.

---

### Post by diepruis on 2006-12-30
You could install two instances of GRUB. One on the SATA disk and one on the IDE drive. The SATA one would be configured with 2 options while the IDE drive's one only has 1. Then set the boot device priority in the BIOS to first the SATA disk, then the IDE disk.

Only thing is, where would the config files for the GRUBs be stored? And would the BIOS complain if the SATA disk went missing?

---

### Post by Raffael on 2006-12-30
There will no problem with BIOS , I've checked. When I set proper booting order SATA/IDE/CDROM and SATA is missing it automatically sets IDE as the first one (as far as I remember).

I don't know how to install 2 instances of GRUB, any help will be useful.

---

### Post by diepruis on 2006-12-31
Neither am I. If noone else more knowledgable is forthcoming, you may want to take a look at the GRUB documentation: [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

Have fun and good luck :)

---

### Post by gn2 on 2006-12-31
By "rack" do you mean a removable hard drive?

Do you want XP to boot by default when the Sata drive is inserted?

If so it could easier to set up than you might think.

Set the boot order in the BIOS so that PC boots from the Sata drive before the IDE drive.

Remove the Sata Windows drive.

Install Ubuntu and Grub to the IDE drive.

And you're done.

More info on two-drive dual booting here: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by diepruis on 2006-12-31
> **gn2 said:**
> Do you want XP to boot by default when the Sata drive is inserted?

No, he wants a boot screen when the XP drive is inserted.

> The problem is that I want the bootloader screen to occur only when my SATA drive (with Windows XP) is in the rack.

---

### Post by gn2 on 2006-12-31
> **diepruis said:**
> No, he wants a boot screen when the XP drive is inserted.

I know that was in the post, but he may be may be unaware that he doesn't require a boot screen if all he wants is to boot XP when it's drive is present.

Which is why I asked the question. :)

---

### Post by diepruis on 2006-12-31
> **gn2 said:**
> I know that was in the post, but he may be may be unaware that he doesn't require a boot screen if all he wants is to boot XP when it's drive is present.

Which is why I asked the question. :)

Okay, no problem. ;)

---

### Post by Raffael on 2006-12-31
Quite nice idea gn2. If it works this way then I will try it.

If I find a way to do it with bootloader screen I will post it here.

Thanks everyone for helping me.

---

### Post by Raffael on 2007-01-02
Sorry for renewing the topic and writing below my previous post, but I've forgot to ask about something.

Will my Ubuntu see the SATA II/300 drive with Windows XP after I install Linux this way?

I know that reading/writing depends on the File System (I'm using NTFS, and yes I'm aware of its incompatibility with Linux systems) so I only want to know if the drive is accesible.

---

