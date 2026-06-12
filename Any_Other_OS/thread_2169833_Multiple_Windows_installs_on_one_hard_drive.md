---
title: "Multiple Windows installs on one hard drive?"
date: 2013-08-23
forum: Any Other OS
---

### Post by Maximus559 on 2013-08-23
We've probably all installed Linux alongside Windows on the same hard drive (with separate partitions, of course). I'm curious whether it's feasible to install multiple instances of the **same** Windows version on the same (partitioned) hard drive. I know I could install, say, Windows 98, Windows 2000, and Windows XP in that order, but this is a somewhat different question.

What I'd like to do is split a hard drive into two, three, or four primary partitions, install Windows XP Professional 32-bit to each one, and then choose between them at boot time. I'm not positive that Windows XP would even let me perform these installs, but assuming it would, I have a few questions:

[LIST]
[*]Would the Windows boot loader be able to handle this arrangement, or would I need to install GRUB?
[*]Would the multiple Windows installs be in danger of interfering with one another?
[*]Would I be limited to four primary partitions? (seems likely)
[*]Do other versions of Windows (e.g., Windows 98 SE) support this configuration?
[/LIST]
I do a lot of testing with old hardware and old device drivers, so having four Windows installs on the same hard drive would be extremely useful.

EDIT: Assume all installs are done on the same machine.

---

### Post by davetv on 2013-08-23
Not possible. Only way is that each hard disk would require its own Windows bootloader and select boot order in bios at boot time. Have you thought about using virtual machines?

---

### Post by oldfred on 2013-08-23
Possible, but legally you have to have a license for every install. It may complain since Windows does keep track.
If only booting Windows, the one partition with the boot flag will have all the boot files and update boot.ini or BCD to let you choose.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Maximus559 on 2013-08-23
> [COLOR=#000000]Have you thought about using virtual machines?[/COLOR]

Not an option, unfortunately. I'll be testing graphics cards and will need hardware-accelerated 3D. Overall system performance is also important.

> [COLOR=#000000]Possible, but legally you have to have a license for every install.[/COLOR]

I should clarify: multiple partitions, multiple Windows installs, **same** system (more or less). Each install might be configured for a different graphics card or sound card, but the motherboard, CPU, and network adapter would remain the same. Windows 7/8 might be different, but Windows XP's activation system shouldn't care. Sequential installs less than 120 days apart might require a phone call to Mumbai, but that's it.

---

